---
title: "multi boot dual hard drives"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dhaulk on 2007-03-09
I have 2 hard drives the primary master has windos xp pro and I wanna run Ubuntu 6.10 and Backtrack2 on the slave. Whats the easiest way to do this? the slave drive is 20gb and the backtrack takes 2.7gb to install. I just reformatted the drive  because I tried to put kismet and aircrack on my ubuntu didn't work out. Then I found backtrack2 which allready has those and a bunch of other good stuff but I like the layout of ubuntu better.

---

### Post by etank on 2007-03-09
Since you have XP on the first drive I would install BackTrack first on the second hard drive. Give it about 8G so it has some room to grow. Then install Ubuntu in the other 12G. I would create three partitions on the Ubuntu install. One each for /, /home and swap. / could be about 4G, /home about 9G and 1G for swap.

The Ubuntu install should take care of creating the grub entries to allow booting into each of the OSs.

---

