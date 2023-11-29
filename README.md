# utl-plot-every-column-against-every-other-column-ggplot-ods-wps
Plot every column of a data frame agains every other ggplot ods wps;
    %let pgm=utl-plot-every-column-against-every-other-column-ggplot-ods-wps;

    Plot every column of a data frame agains every other ggplot ods wps;

        1. ods wps graphics
        2. r ggplot
           https://stackoverflow.com/users/6851825/jon-spring
           
    WPS output
    https://tinyurl.com/3m495yrc
    https://github.com/rogerjdeangelis/utl-plot-every-column-against-every-other-column-ggplot-ods-wps/blob/main/allCmb.pdf

    R output
    https://tinyurl.com/3d6259km
    https://github.com/rogerjdeangelis/utl-plot-every-column-against-every-other-column-ggplot-ods-wps/blob/main/allCmb_r.pdf

    github
    https://tinyurl.com/2xwfja6z
    https://github.com/rogerjdeangelis/utl-plot-every-column-against-every-other-column-ggplot-ods-wps

    SOAPBOX ON

      WPS and R take different approaches to graphics (they complement each other)

         a. R graphics is most often based on graphic layers. You bulid your graph in layers.
         b. Except for Graph Template Language, WPS provides easy to use procs
            that handle 90%? of a users need.

    SOAPBOX OFF

    github
    https://tinyurl.com/muxz7mdr
    https://stackoverflow.com/questions/77567613/how-to-plot-every-column-of-a-data-frame-agains-every-other-column-using-ggplot

    https://stackoverflow.com/users/6851825/jon-spring

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

          1        2        3        4  -5             0             1   2        3        4          5
         --+--------+--------+--------+--+-------------+-------------+---+--------+--------+--------+--
         |                              |                              |                              |
       2 +                              |               A   A          |                  AA          +  2
         |                              |     A  A   A                 |                  AA  A       |
         |              _               |                A     A       |                  A  A        |
         |             / \              |    A             A  AB AA  A |           A    AA BBA        |
       0 +            / _ \             |            A   B  A     A    |              A    BA  A      +  0
         |           / ___ \            |   A       A      AA A A      |  A            AA A  A A      |
         |          /_/   \_\           |                   A          |                        A     |
         |                              |                              |                              |
      -2 +                              |             A        A       |                  AA          + -2
         |                              |    A    A                    |                     A      A |
         |                              |                              |                              |
         |                              |                              |                              |
      -4 +                              |                              |                              + -4
         |                              |                              |                              |
         ----------------------------------------------------------------------------------------------
         |                              |                              |                              |
       2 +                  AA          |                              |                  AA          +  2
         |                  AA  A       |                              |                  AA  A       |
         |                  A  A        |                              |                  A  A        |
         |           A    AA BBA        |           ____               |           A    AA BBA        |
       0 +              A    BA  A      |          | __ )              |              A    BA  A      +  0
         |  A            AA A  A A      |          |  _ \              |  A            AA A  A A      |
         |                        A     |          | |_) |             |                        A     |
         |                              |          |____/              |                              |
      -2 +                  AA          |                              |                  AA          + -2
         |                     A      A |                              |                     A      A |
         |                              |                              |                              |
         |                              |                              |                              |
      -4 +                              |                              |                              + -4
         |                              |                              |                              |
         ----------------------------------------------------------------------------------------------
         |                              |                              |                              |
       2 +                   AA         |               A   A          |                              +  2
         |                   AA  A      |     A  A   A                 |                              |
         |                   A  A       |                A     A       |                              |
         |            A    AA BBA       |    A             A  AB AA  A |           ____               |
       0 +               A    BA  A     |            A   B  A     A    |          / ___|              +  0
         |   A            AA A  A A     |   A       A      AA A A      |         | |                  |
         |                         A    |                   A          |         | |___               |
         |                              |                              |          \____|              |
      -2  +                  AA         |   |         A        A       |                              + -2
         |                      A       |    A    A                    |                              |
         |                              |                              |                              |
         |                              |                              |                              |
      -4 +                              |                          |   |                              + -4
         |                              |                              |                              |
         --+--------+--------+--------+--+-------------+-------------+---+--------+--------+---------=+
           1        2        3        4  -5            0             1   2        3        4          5

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
      input a b c;
      id=_n_;
    cards4;
    -2.46 3.27 -3.54
     0.40 3.07  4.97
     1.67 2.91 -1.98
    -0.42 2.90  3.09
    -2.44 3.99 -1.76
     0.35 2.78 -3.52
     2.08 2.88  0.18
     0.05 3.04  1.81
    -0.29 1.16 -0.99
    -0.57 2.50 -3.87
     0.60 3.01  2.43
     0.44 3.17  1.31
     0.19 3.04 -0.66
    -1.84 2.97  1.39
    -0.66 3.27  1.26
    -1.87 2.89 -1.69
     0.24 2.43  3.89
     1.37 3.02 -0.58
     0.66 2.70  2.84
     1.15 2.88  2.69
     0.02 3.16  0.62
     0.17 3.46  0.80
     0.86 3.26  0.84
    -0.63 2.72  2.59
     0.30 2.12  3.55
    -0.33 3.39  1.61
     1.91 3.03  1.76
     0.41 2.96  2.81
    -1.14 3.59  1.95
     0.62 3.11  3.84
     1.55 3.30 -3.08
    ;;;;
    run;quit;

    /*                                  _                             _     _
    / | __      ___ __  ___    ___   __| |___    __ _ _ __ __ _ _ __ | |__ (_) ___ ___
    | | \ \ /\ / / `_ \/ __|  / _ \ / _` / __|  / _` | `__/ _` | `_ \| `_ \| |/ __/ __|
    | |  \ V  V /| |_) \__ \ | (_) | (_| \__ \ | (_| | | | (_| | |_) | | | | | (__\__ \
    |_|   \_/\_/ | .__/|___/  \___/ \__,_|___/  \__, |_|  \__,_| .__/|_| |_|_|\___|___/
                 |_|                            |___/          |_|
    */


    %utlfkil(d:/pdf/allCmb_wps.pdf);

    %utl_submit_wps64x('
    libname sd1 "d:/sd1";
    ods pdf file="d:/pdf/allCmb_wps.pdf";
    proc sgscatter data=sd1.have;
    matrix a b c;
    run;quit;
    ods pdf close;
    ');

    /*___                             _       _
    |___ \   _ __    __ _  __ _ _ __ | | ___ | |_
      __) | | `__|  / _` |/ _` | `_ \| |/ _ \| __|
     / __/  | |    | (_| | (_| | |_) | | (_) | |_
    |_____| |_|     \__, |\__, | .__/|_|\___/ \__|
                    |___/ |___/|_|
    */

    %utlfkil(d:/pdf/allCmb_r.pdf);

    %utl_submit_wps64x('
    libname sd1 "d:/sd1";
    proc r;
    export data=sd1.have r=have;
    submit;
    library(tidyverse);
    have;
    have_long <- pivot_longer(have, -ID);
    pdf("d:/pdf/allCmb_r.pdf");
    have_long |>
      left_join(have_long, join_by(ID)) |>
      ggplot(aes(value.x, value.y)) +
      geom_point() +
      facet_grid(name.y ~ name.x);
    pdf();
    endsubmit;
    ');

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
