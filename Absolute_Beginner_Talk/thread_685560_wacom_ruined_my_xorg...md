---
title: "wacom ruined my xorg.."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-02-02
well... i tried to make my waom work and by doing this my xorg wouldnt start i had to 

sudo dpkg-reconfigure -phigh xerver-xorg

and now i dont know how to make it work withot damaging xorg

---

### Post by patchido on 2008-02-02
i am trying to open up synaptic and this pops up.... damn it> failed to run /usr/sbin/synaptic

unable to copy th user's Xauthorization file.

---

### Post by taurus on 2008-02-02
You can try running, from a terminal

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post the output of this command since it complains about .Xauthorization in your $HOME.

```
ls -la ~
```

---

### Post by patchido on 2008-02-02
> **taurus said:**
> You can try running, from a terminal

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post the output of this command since it complains about .Xauthorization in your $HOME.

```
ls -la ~
```

```
total 26779204
drwxr-xr-x 72 pato pato      20480 2008-02-02 09:55 .
drwxr-xr-x  3 root root       4096 2008-01-09 05:11 ..
drwx------  3 pato pato       4096 2008-01-09 13:13 .adobe
drwx------  5 pato pato       4096 2008-01-10 17:37 .aria
drwxr-xr-x  2 pato pato       4096 2008-02-01 15:15 autosave
drwxr-xr-x  4 pato pato       4096 2008-01-12 11:33 .autumn
drwxr-xr-x 14 pato pato       4096 2008-01-10 14:13 awn-curves
-rw-------  1 pato pato       3596 2008-02-02 09:31 .bash_history
-rw-r--r--  1 pato pato        220 2008-01-09 05:11 .bash_logout
-rw-r--r--  1 pato pato       2298 2008-01-09 05:11 .bashrc
drwxr-xr-x  5 pato pato       4096 2008-02-01 15:08 .blender
-rw-r--r--  1 pato pato     119077 2008-01-10 14:09 .bzr.log
drwxr-xr-x  3 pato pato       4096 2008-01-09 11:52 .cache
drwxr-xr-x  5 pato pato       4096 2008-01-27 20:21 compiz
drwxr-xr-x  5 root root       4096 2008-01-12 11:33 .compiz
drwxr-xr-x  9 pato pato       4096 2008-01-28 09:43 .config
-rw-r--r--  1 pato pato       4956 2008-01-28 12:15 crashinfo.txt
drwxr-xr-x  3 pato pato       4096 2008-02-01 06:53 Desktop
-rw-r--r--  1 pato pato         40 2008-01-27 23:30 .devede
-rw-r--r--  1 pato pato     117364 2008-01-13 18:26 dilbert.gif
-rw-------  1 pato pato         28 2008-02-01 23:58 .dmrc
-rw-r--r--  1 pato pato  102000000 2008-01-17 12:06 DN10TW.part1.rar
-rw-r--r--  1 pato pato   78777392 2008-01-17 12:19 DN10TW.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 12:33 DN11TW.part1.rar
-rw-r--r--  1 pato pato   79004912 2008-01-17 12:44 DN11TW.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 13:02 DN12TW.part1.rar
-rw-r--r--  1 pato pato   78901184 2008-01-17 13:15 DN12TW.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 13:30 DN13.part1.rar
-rw-r--r--  1 pato pato   78888948 2008-01-17 13:41 DN13.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 13:56 DN14.part1.rar
-rw-r--r--  1 pato pato   78868620 2008-01-17 14:08 DN14.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 14:23 DN15.part1.rar
-rw-r--r--  1 pato pato   92697052 2008-01-17 14:52 DN15.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 15:09 DN16.part1.rar
-rw-r--r--  1 pato pato   79849004 2008-01-17 15:22 DN16.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 15:38 DN17.part1.rar
-rw-r--r--  1 pato pato   62680678 2008-01-17 15:47 DN17.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 16:05 DN18.part1.rar.html
-rw-r--r--  1 pato pato   52318326 2008-01-17 16:14 DN18.part2.rar.html
-rw-r--r--  1 pato pato  102000000 2008-01-17 16:33 DN19.part1.rar.html
-rw-r--r--  1 pato pato   71779606 2008-01-17 16:47 DN19.part2.rar.html
-rw-r--r--  1 pato pato  102000000 2008-01-17 17:02 DN20.part1.rar.html
-rw-r--r--  1 pato pato   60526016 2008-01-17 17:12 DN20.part2.rar.html
-rw-r--r--  1 pato pato  102000000 2008-01-17 17:56 DN22.part1.rar
-rw-r--r--  1 pato pato   53023806 2008-01-17 18:04 DN22.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 18:19 DN23.part1.rar
-rw-r--r--  1 pato pato   53953518 2008-01-17 18:28 DN23.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 22:13 DN24.part1.rar
-rw-r--r--  1 pato pato   83674350 2008-01-17 22:33 DN24.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 22:48 DN25.part1.rar
-rw-r--r--  1 pato pato   80584222 2008-01-17 22:59 DN25.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 23:14 DN26.part1.rar
-rw-r--r--  1 pato pato   85010926 2008-01-17 23:27 DN26.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 23:55 DN27.part1.rar
-rw-r--r--  1 pato pato   82397470 2008-01-18 00:07 DN27.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 00:22 DN28.part1.rar
-rw-r--r--  1 pato pato   47731990 2008-01-18 00:29 DN28.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 00:43 DN29.part1.rar
-rw-r--r--  1 pato pato   88101486 2008-01-18 00:56 DN29.part2.rar
-rw-r--r--  1 pato pato  100000000 2008-01-17 08:09 DN2.part1.rar
-rw-r--r--  1 pato pato   80965200 2008-01-17 08:21 DN2.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 01:10 DN30.part1.rar
-rw-r--r--  1 pato pato   88178884 2008-01-18 01:23 DN30.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 01:38 DN31.part1.rar
-rw-r--r--  1 pato pato   83515774 2008-01-18 01:50 DN31.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 02:04 DN32.part1.rar
-rw-r--r--  1 pato pato   78190472 2008-01-18 02:15 DN32.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 02:30 DN33.part1.rar
-rw-r--r--  1 pato pato   79660974 2008-01-18 02:41 DN33.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 02:56 DN34.part1.rar
-rw-r--r--  1 pato pato   74205134 2008-01-18 03:06 DN34.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 03:21 DN35.part1.rar
-rw-r--r--  1 pato pato   79019070 2008-01-18 03:32 DN35.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 03:47 dn36.part1.rar
-rw-r--r--  1 pato pato   91766500 2008-01-18 04:00 dn36.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-18 04:15 DN37.part1.rar
-rw-r--r--  1 pato pato   81333206 2008-01-18 04:26 DN37.part2.rar
-rw-r--r--  1 pato pato  100000000 2008-01-17 08:35 DN3.part1.rar
-rw-r--r--  1 pato pato   81183888 2008-01-17 08:47 DN3.part2.rar
-rw-r--r--  1 pato pato  104000000 2008-01-17 09:02 DN4.part1.rar
-rw-r--r--  1 pato pato   77025120 2008-01-17 09:14 DN4.part2rar
-rw-r--r--  1 pato pato  104000000 2008-01-17 09:29 DN5.part1.rar
-rw-r--r--  1 pato pato   77052704 2008-01-17 09:40 DN5.part2.rar
-rw-r--r--  1 pato pato  104000000 2008-01-17 09:55 DN6.part1.rar
-rw-r--r--  1 pato pato   76720192 2008-01-17 10:06 DN6.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 10:22 DN7.part1.rar
-rw-r--r--  1 pato pato   79001816 2008-01-17 10:33 DN7.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 10:48 DN8.part1.rar
-rw-r--r--  1 pato pato   78937560 2008-01-17 10:59 DN8.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 11:40 DN9LE.part1.rar
-rw-r--r--  1 pato pato   78999194 2008-01-17 11:51 DN9LE.part2.rar
-rw-r--r--  1 pato pato  102000000 2008-01-17 11:14 DN9TWrar.part1.rar
-rw-r--r--  1 pato pato   79174416 2008-01-17 11:25 DN9TWrar.part2.rar
drwxr-xr-x 11 pato pato       4096 2008-02-02 00:24 Documents
-rw-r--r--  1 pato pato  102000000 2008-01-17 17:29 DTHNTE21.part1.rar
-rw-r--r--  1 pato pato   83107086 2008-01-17 17:41 DTHNTE21.part2.rar
-rw-r--r--  1 pato pato  178626560 2007-04-16 12:00 [Eclipse] Claymore - 01 (XviD) [EAB5EFF5].avi
-rw-r--r--  1 pato pato  178616320 2007-04-16 10:49 [Eclipse] Claymore - 02 (XviD) [3B883489].avi
-rw-r--r--  1 pato pato  178644992 2007-04-19 09:49 [Eclipse] Claymore - 03 (XviD) [846EE465].avi
-rw-r--r--  1 pato pato  178468864 2007-04-25 20:46 [Eclipse] Claymore - 04 (XviD) [84DEB594].avi
-rw-r--r--  1 pato pato  177317888 2007-05-03 00:23 [Eclipse] Claymore - 05 (XviD) [ABACAC9E].avi
-rw-r--r--  1 pato pato  178616320 2007-05-10 13:26 [Eclipse] Claymore - 06 (XviD) [DB5ABE8C].avi
-rw-r--r--  1 pato pato  180512768 2007-05-16 20:15 [Eclipse] Claymore - 07 (XviD) [0C04E843].avi
-rw-r--r--  1 pato pato  244666368 2007-05-23 19:45 [Eclipse] Claymore - 08 (XviD) [745E9180].avi
-rw-r--r--  1 pato pato  178610176 2007-05-30 21:38 [Eclipse] Claymore - 09 (XviD) [1DD97D99].avi
-rw-r--r--  1 pato pato  178608128 2007-06-07 11:05 [Eclipse] Claymore - 10 (XviD) [480195D8].avi
-rw-r--r--  1 pato pato  177070080 2007-06-14 18:54 [Eclipse] Claymore - 11 (XviD) [0D71B675].avi
-rw-r--r--  1 pato pato  177082368 2007-06-20 18:55 [Eclipse] Claymore - 12 (XviD) [D5A2E61A].avi
-rw-r--r--  1 pato pato  177072128 2007-06-27 20:02 [Eclipse] Claymore - 13 (XviD) [299DF6C3].avi
-rw-r--r--  1 pato pato  177082368 2007-07-04 19:12 [Eclipse] Claymore - 14 (XviD) [4147262B].avi
-rw-r--r--  1 pato pato  176848896 2007-07-11 19:09 [Eclipse] Claymore - 15 (XviD) [D17FBE7A].avi
-rw-r--r--  1 pato pato  177080320 2007-07-18 19:11 [Eclipse] Claymore - 16 (XviD) [3C884416].avi
-rw-r--r--  1 pato pato  176865280 2007-07-26 06:43 [Eclipse] Claymore - 17 (XviD) [40AFE84B].avi
-rw-r--r--  1 pato pato  177623040 2007-08-02 07:08 [Eclipse] Claymore - 18 (XviD) [322FAA67].avi
-rw-r--r--  1 pato pato  178769920 2007-08-09 18:35 [Eclipse] Claymore - 19 (XviD) [A4D7A5B2].avi
-rw-r--r--  1 pato pato  177070080 2007-08-18 08:32 [Eclipse] Claymore - 20 (XviD) [26647CEA].avi
-rw-r--r--  1 pato pato  177096704 2007-08-22 18:24 [Eclipse] Claymore - 21 (XviD) [355A4F0B].avi
-rw-r--r--  1 pato pato  176869376 2007-08-30 18:02 [Eclipse] Claymore - 22 (XviD) [14E4C7B3].avi
-rw-r--r--  1 pato pato  182478848 2007-09-05 21:20 [Eclipse] Claymore - 23 (XviD) [BC50C579].avi
-rw-r--r--  1 pato pato  177106944 2007-09-13 06:44 [Eclipse] Claymore - 24 (XviD) [F3A70354].avi
-rw-r--r--  1 pato pato  177065984 2007-09-19 17:30 [Eclipse] Claymore - 25 (XviD) [2D40C153].avi
-rw-r--r--  1 pato pato  180840448 2007-09-26 17:54 [Eclipse] Claymore - 26 (XviD) [3AFB08CA].avi
-rw-r--r--  1 pato pato  104857600 2008-01-31 15:57 enjoy.this.great.up.greetz.slisher.part01.rar
-rw-r--r--  1 pato pato  104857600 2008-01-31 16:14 enjoy.this.great.up.greetz.slisher.part02.rar
-rw-r--r--  1 pato pato  104857600 2008-01-31 22:19 enjoy.this.great.up.greetz.slisher.part03.rar
-rw-r--r--  1 pato pato  104857600 2008-01-31 22:40 enjoy.this.great.up.greetz.slisher.part04.rar
-rw-r--r--  1 pato pato  104857600 2008-01-31 23:45 enjoy.this.great.up.greetz.slisher.part05.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 06:56 enjoy.this.great.up.greetz.slisher.part06.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 15:30 enjoy.this.great.up.greetz.slisher.part07.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 15:50 enjoy.this.great.up.greetz.slisher.part08.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 16:29 enjoy.this.great.up.greetz.slisher.part09.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 16:45 enjoy.this.great.up.greetz.slisher.part10.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 17:00 enjoy.this.great.up.greetz.slisher.part11.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 17:15 enjoy.this.great.up.greetz.slisher.part12.rar
-rw-r--r--  1 pato pato  104857600 2008-02-01 17:31 enjoy.this.great.up.greetz.slisher.part13.rar
-rw-r--r--  1 pato pato   57543552 2008-02-01 18:20 enjoy.this.great.up.greetz.slisher.part14.rar
-rw-r--r--  1 pato pato     462848 2008-01-23 15:18 Escuadra Maoris.doc
-rw-------  1 pato pato         16 2008-01-09 11:53 .esd_auth
drwxr-xr-x  7 pato pato       4096 2008-02-02 00:47 .evolution
lrwxrwxrwx  1 pato pato         26 2008-01-09 05:11 Examples -> /usr/share/example-content
-rw-r--r--  1 pato pato  811028400 2007-10-25 16:22 FF8_Disc1.iso
-rw-r--r--  1 pato pato  645863904 2007-10-25 16:22 FF8_Disc2.iso
-rw-r--r--  1 pato pato  100431872 2008-01-28 00:33 FF8_Disc2.part1.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 00:48 FF8_Disc2.part2.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 01:04 FF8_Disc2.part3.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 01:19 FF8_Disc2.part4.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 01:34 FF8_Disc2.part5.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 01:49 FF8_Disc2.part6.rar
-rw-r--r--  1 pato pato   43273302 2008-01-28 01:56 FF8_Disc2.part7.rar
drwx------  2 pato pato       4096 2008-01-31 16:02 FF8_Disc3.part1
-rw-r--r--  1 pato pato  100431872 2008-01-28 02:11 FF8_Disc3.part1.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 02:26 FF8_Disc3.part2.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 02:42 FF8_Disc3.part3.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 02:57 FF8_Disc3.part4.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 03:13 FF8_Disc3.part5.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 03:28 FF8_Disc3.part6.rar
-rw-r--r--  1 pato pato   28594216 2008-01-28 03:32 FF8_Disc3.part7.rar
-rw-r--r--  1 pato pato  789827472 2007-10-25 16:23 FF8_Disc4.iso
-rw-r--r--  1 pato pato  100431872 2008-01-28 03:47 FF8_Disc4.part1.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 04:03 FF8_Disc4.part2.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 04:18 FF8_Disc4.part3.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 04:33 FF8_Disc4.part4.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 04:48 FF8_Disc4.part5.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 05:04 FF8_Disc4.part6.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 05:19 FF8_Disc4.part7.rar
-rw-r--r--  1 pato pato   86805088 2008-01-28 05:32 FF8_Disc4.part8.rar
-rw-r--r--  1 pato pato  652851696 2007-10-25 16:22 FF8_Install.iso
-rw-r--r--  1 pato pato  100431872 2008-01-28 05:47 FF8_Install.part1.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 06:02 FF8_Install.part2.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 06:17 FF8_Install.part3.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 06:32 FF8_Install.part4.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 06:47 FF8_Install.part5.rar
-rw-r--r--  1 pato pato  100431872 2008-01-28 10:07 FF8_Install.part6.rar
-rw-r--r--  1 pato pato   50261108 2008-01-28 15:50 FF8_Install.part7.rar
drwxr-xr-x  2 pato pato       4096 2008-02-01 14:53 .fontconfig
drwx------  2 pato pato      45056 2008-01-13 22:50 .gcjwebplugin
drwx------  5 pato pato       4096 2008-02-02 09:55 .gconf
drwx------  2 pato pato       4096 2008-02-02 10:24 .gconfd
drwx------  2 pato pato       4096 2008-01-31 23:22 .ggz
drwxr-xr-x 22 pato pato       4096 2008-01-25 11:26 .gimp-2.4
-rw-r-----  1 pato pato          0 2008-02-02 00:09 .gksu.lock
-rw-r--r--  1 pato pato      29129 2008-01-16 14:28 gls_karol39@hotmail.com.png
drwxr-xr-x  3 pato pato       4096 2008-01-09 11:52 .gnome
drwx------ 18 pato pato       4096 2008-02-02 00:44 .gnome2
drwx------  2 pato pato       4096 2008-01-09 11:52 .gnome2_private
drwxr-xr-x  2 pato pato       4096 2008-02-01 11:04 .gstreamer-0.10
-rw-r--r--  1 pato pato        104 2008-02-02 09:55 .gtk-bookmarks
-rw-r--r--  1 pato pato         86 2008-01-09 11:52 .gtkrc-1.2-gnome2
drwxr-----  2 root root       4096 2008-01-14 23:07 .hplip
-rw-r--r--  1 pato pato      35529 2008-01-30 22:21 hs_err_pid11306.log
-rw-------  1 pato pato       8347 2008-02-02 09:55 .ICEauthority
drwxr-xr-x  3 pato pato       4096 2008-01-10 15:21 .icons
drwxr-xr-x  2 pato pato       4096 2008-02-01 15:16 .jamin
drwxr-xr-x  3 pato pato       4096 2008-01-30 22:02 .java
drwxr-xr-x  8 pato pato       4096 2008-02-01 11:04 .jokosher
drwx------  3 pato pato       4096 2008-01-12 11:26 .kde
drwx------  2 pato pato       4096 2008-01-30 14:20 .kino-history
-rw-r--r--  1 pato pato       2968 2008-01-30 15:34 .kinorc
drwxr-xr-x  5 pato pato       4096 2008-02-02 00:29 linuxwacom-0.7.8-3
-rw-r--r--  1 pato pato    1002452 2008-02-02 00:24 linuxwacom-0.7.8-3.tar.bz2
-rw-------  1 pato pato      66004 2008-01-17 23:51 list
-rw-------  1 pato pato     244570 2008-01-25 16:30 listtt
drwxr-xr-x  3 pato pato       4096 2008-01-09 11:52 .local
drwx------  3 pato pato       4096 2008-01-09 13:13 .macromedia
-rw-r--r--  1 pato pato 4642889728 2007-12-01 21:40 made-bender.iso
-rw-r--r--  1 pato pato       2047 2008-01-14 23:33 .mailcap
drwxr-xr-x  3 pato pato       4096 2008-01-27 15:16 .mcop
-rw-------  1 pato pato         31 2008-02-01 15:06 .mcoprc
drwx------  3 pato pato       4096 2008-01-09 14:56 .metacity
drwxr-xr-x  2 pato pato       4096 2008-01-27 10:35 .metagui
-rw-r--r--  1 pato pato 1587429376 2008-01-28 04:45 movie.iso
drwx------  4 pato pato       4096 2008-01-10 16:02 .mozilla
drwx------  3 pato pato       4096 2008-01-10 16:02 .mozilla-thunderbird
drwx------  2 pato pato       4096 2008-01-24 16:14 .mplayer
drwxr-xr-x  2 pato pato       4096 2008-01-16 17:25 .mumbles
drwxr-xr-x 11 pato pato       4096 2008-01-31 22:49 Music
drwxr-xr-x  3 pato pato       4096 2008-02-01 11:28 .nautilus
-rw-r--r--  1 pato pato     151552 2008-01-21 14:51 nautilus-debug-log.txt
drwxr-xr-x  3 pato pato       4096 2008-01-27 14:09 .ogle
drwx------  3 pato pato       4096 2008-01-30 23:19 .openoffice.org2
drwxr-xr-x  3 pato pato       4096 2008-02-01 11:04 paa
-rw-r--r--  1 pato pato   14872957 2008-02-01 11:27 pato.wpp;
drwxr-xr-x  2 pato pato       4096 2008-01-09 11:52 Pictures
-rw-r--r--  1 pato pato     548352 2008-01-25 15:29 PlaneacionEnero-Febrero2008Hunter.doc
-rw-r--r--  1 pato pato  104857600 2008-01-27 17:28 POP3D.part01.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 17:46 POP3D.part02.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 18:03 POP3D.part03.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 18:25 POP3D.part04.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 18:43 POP3D.part05.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 18:59 POP3D.part06.rar
-rw-r--r--  1 pato pato  104857600 2008-01-27 19:17 POP3D.part07.rar
-rw-r--r--  1 pato pato   38075744 2008-01-27 19:25 POP3D.part08.rar
drwxr-xr-x  5 pato pato       4096 2007-09-16 14:29 Prince Of Persia 3D (RedOrb)
-rw-r--r--  1 pato pato        566 2008-01-09 05:11 .profile
drwxr-xr-x  2 pato pato       4096 2008-01-09 11:52 Public
drwx------  7 pato pato       4096 2008-02-02 10:23 .purple
drwxr-xr-x  2 pato pato       4096 2008-01-28 15:52 .qt
drwxr-sr-x 11 root root       4096 2008-01-14 23:31 Real
-rw-r--r--  1 pato pato      34554 2008-01-14 23:33 .realplayerrc
-rw-------  1 pato pato       5528 2008-01-30 23:19 .recently-used
-rw-r--r--  1 pato pato     144005 2008-02-02 00:44 .recently-used.xbel
-rw-------  1 root root       1024 2008-01-15 15:47 .rnd
drwxr-xr-x  2 pato pato       4096 2008-01-31 15:37 .screenlets
-rw-------  1 pato pato         56 2008-02-02 09:55 .serverauth.5913
-rw-------  1 pato pato        112 2008-01-17 22:03 .serverauth.6650
-rw-------  1 pato pato        168 2008-01-21 11:11 .serverauth.7248
drwxr-xr-x  2 pato pato       4096 2008-01-27 12:58 .spumux
drwx------  2 pato pato       4096 2008-01-25 10:35 .ssh
-rw-r--r--  1 pato pato          0 2008-01-09 12:07 .sudo_as_admin_successful
drwxr-xr-x  2 pato pato       4096 2008-01-09 11:52 Templates
-rw-r--r--  1 pato pato     244570 2008-01-25 16:30 .temporary.working
drwxr-xr-x  2 pato pato       4096 2008-01-10 15:21 .themes
-rw-r--r--  1 pato pato  767190247 2007-12-06 22:31 the_simpsons_movie_x264_uSk.mkv
drwx------  5 pato pato       4096 2008-02-01 06:53 .thumbnails
-rw-r--r--  1 pato pato        681 2008-01-10 14:11 (tik).png
drwxr-xr-x  4 pato pato       4096 2008-01-30 22:51 .tomboy
-rw-r--r--  1 pato pato       4815 2008-01-30 23:55 .tomboy.log
drwxr-xr-x  2 pato pato       4096 2008-01-27 11:54 .tovid
drwx------  2 pato pato       4096 2008-02-01 14:38 .Trash
-rw-r--r--  1 pato pato  183158784 2006-10-16 21:26 [TW]_Death_Note_EP01_[9B72C4DD].avi
-rw-r--r--  1 pato pato  183238656 2006-10-16 21:20 [TW]_Death_Note_EP02_[AB249DDA].avi
drwxr-xr-x  2 pato pato       4096 2008-01-09 12:06 .update-manager-core
drwx------  2 pato pato       4096 2008-01-15 00:33 .update-notifier
drwxr-xr-x  2 pato pato       4096 2008-01-09 11:52 Videos
drwxr-xr-x  2 pato pato       4096 2008-01-30 23:02 .vmware
drwx------  2 pato pato       4096 2008-01-14 23:31 .w3m
drwxr-xr-x  2 pato pato       4096 2008-02-01 06:53 .wapi
drwx------  2 pato pato       4096 2008-01-31 22:55 WavePad_3.05___Keygen
-rw-r--r--  1 pato pato     446734 2008-01-31 22:55 WavePad_3.05___Keygen.rar
drwx------  2 pato pato       4096 2008-01-15 00:25 webexpression2007_celebiyiz.biz.part1
-rw-r--r--  1 pato pato  100431872 2008-01-15 00:07 webexpression2007_celebiyiz.biz.part1.rar
-rw-r--r--  1 pato pato  100431872 2008-01-15 00:22 webexpression2007_celebiyiz.biz.part2.rar
-rw-r--r--  1 pato pato    4404527 2008-01-15 00:23 webexpression2007_celebiyiz.biz.part3.rar
-rw-r--r--  1 pato pato  100000000 2008-01-10 18:07 WiLLieST_Basket.part1.rar
-rw-r--r--  1 pato pato  100000000 2008-01-12 11:53 WiLLieST_Basket.part2.rar
-rw-r--r--  1 pato pato  100000000 2008-01-11 14:43 WiLLieST_Basket.part3.rar
-rw-r--r--  1 pato pato  100000000 2008-01-11 14:27 WiLLieST_Basket.part4.rar
-rw-r--r--  1 pato pato  100000000 2008-01-12 12:14 WiLLieST_Basket.part5.rar
-rw-r--r--  1 pato pato  100000000 2008-01-10 18:33 WiLLieST_Basket.part6.rar
-rw-r--r--  1 pato pato   84040170 2008-01-10 18:19 WiLLieST_Basket.part7.rar
drwxr-xr-x  4 pato pato       4096 2008-02-01 11:27 .wine
-rw-------  1 root root         49 2008-02-02 00:51 .Xauthority
-rw-------  2 pato pato          0 2008-02-02 09:55 .Xauthority-c
-rw-------  2 pato pato          0 2008-02-02 09:55 .Xauthority-l
-rw-------  1 pato pato      28408 2008-02-02 10:23 .xsession-errors

```

didnt work.. that is the outcome|

---

### Post by taurus on 2008-02-02
Somehow, /home/pato/.Xauthority is owned by root.  It should be owned by you, pato.  So, run

```
sudo chown pato:pato /home/pato/.Xauthority
```
Now, see if you an open synaptic again.

```
gksudo synaptic
```

---

### Post by patchido on 2008-02-02
thx a lot worked fine

---

