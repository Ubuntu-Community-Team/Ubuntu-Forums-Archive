---
title: "labels in gmt"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by eliora on 2007-06-07
i have a file with three columns (latitude longitude and labels for coordinates)
i want to make the third column labels show up on the map and correspond to their coordinates

how do i do that?

psxy stationkiholobay  -: -R$bds  -J$scl -St0.05 -W/0/0/0 -G0/0/0 -V -P -O  >> $outf


that is my line of text for the gmt file but it only puts in the first two columns...
i tried +Lf for the third to be added but it did not work
any advice?

---

