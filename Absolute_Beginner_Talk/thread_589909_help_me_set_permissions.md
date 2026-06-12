---
title: "help me set permissions"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-10-24
I know this has been covered ad naseum but I still do not get it.

situation:

one computer

4 users - me, the wife, and 2 kids


what I want is to be able to access the kids files.

user aron has photos I would like to look at. I can log on with his password but I do not want to. I want to see them when logged on to my own account.

yes, I could use 

```
gksudo nautilus
```

but that is a bit too much.... I just want to access, not get there as root.

I have set up the kids with no admin tasks.... if that matters in this case.

I assume this is all an issuer pertaining to what permissions the users have, which I need to  have in order to have full access.

how to set this up?

thanks

robi

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-24
I have not played with this to much but I think if you change you change the permision on all of your sons files to include group access and then change you and your boys to the same group.
This would give you access to there files.

If you need more info ummm i could try and figure it out ....  some day i am shur i will need this

---

### Post by evilregis on 2007-10-24
Do you want him and the others to be able to see your files (pics) as well or is this one-way only?

---

### Post by beanco on 2007-10-24
It's one way for now.

I want complete access to their stuff and they to not have access to my stuff.

eventually I will have stuff up that they can look at, use, access.. but now I just have important work files, translations etc that I do not want them getting into and making changes to by accident....

robi

---

### Post by p_quarles on 2007-10-24
Do you need read-only access, or read/write access?

Either way, could you post the results of the following command:
```
ls -l ~/*username*
```
where *username* is one of the kids' accounts.

---

### Post by beanco on 2007-10-24
read, write, execute everything....

here is what i got

```
rob@rob-desktop:~$ ls -l ~/aron
ls: /home/rob/aron: No such file or directory
rob@rob-desktop:~$ 

```


which is very confusing since I know the user exists...

what does that squiggly line before / mean, BTW?

robi

---

### Post by p_quarles on 2007-10-24
My bad. It should be:
```
ls -l /home/aron
```
The tilde represents *your *home directory, so the command I gave you was looking for "aron" inside your user's folder.

---

### Post by beanco on 2007-10-24
OK, so  aron is not in my folder he is in

aron@aron


is this not how it should be?


robi

---

### Post by p_quarles on 2007-10-24
Not sure I understand what you mean. Like I said, I mistakenly gave the wrong command in the first message, and I'm presuming that aron's folder is in the correct place. Did the second command I gave not work either?

---

### Post by beanco on 2007-10-24
sorry, did not see your second command

this is what I got


```
rob@rob-desktop:~$ ls -l /home/aron
total 358692
-rw-r--r-- 1 aron aron       0 2007-10-23 14:15 180 ollie.JPG
-rw-r--r-- 1 aron aron    3616 2007-10-04 14:58 BEAT.aup
-rw-r--r-- 1 aron aron     885 2007-10-04 14:41 BEAT.aup~
drwxrwxr-x 2 aron aron   20480 2007-10-04 15:02 BEAT_data
-rw-r--r-- 1 aron aron      96 2007-10-15 14:53 cgmkhfhf
-rw-r--r-- 1 aron aron  409044 2007-10-19 15:49 chiicken.jpg
-rw-r--r-- 1 aron aron  124462 2007-10-19 15:44 cinemabox.jpg
drwxr-xr-x 2 aron aron    4096 2007-10-24 17:17 Desktop
-rw-r--r-- 1 aron aron 2031404 2007-10-05 15:25 drum drum.wav
-rw-r--r-- 1 aron aron 1397804 2007-10-05 15:24 drum.wav
lrwxrwxrwx 1 aron aron      26 2007-10-02 18:10 Examples -> /usr/share/example-content
-rw-r--r-- 1 aron aron     269 2007-10-18 16:48 fykyukyt
drwxr-xr-x 2 aron aron    4096 2007-10-19 16:42 gggtth
-rw-r--r-- 1 aron aron    3010 2007-10-03 18:24 home made music.aup
drwxr-xr-x 3 aron aron    4096 2007-10-18 16:30 MUUSIC
-rw-r--r-- 1 aron aron   12334 2007-10-23 13:48 nautilus-debug-log.txt
-rwx------ 1 aron aron 2257399 2007-10-09 01:19 P1000042.JPG
-rwx------ 1 aron aron 1355578 2007-10-09 01:21 P1000046.JPG
-rwx------ 1 aron aron 1988767 2007-10-09 01:23 P1000049.JPG
-rwx------ 1 aron aron 2106562 2007-10-09 01:24 P1000050.JPG
-rwx------ 1 aron aron 1821054 2007-10-09 02:53 P1000052.JPG
-rwx------ 1 aron aron 1806730 2007-10-09 04:44 P1000056.JPG
-rwx------ 1 aron aron 1856455 2007-10-09 04:44 P1000057.JPG
-rwx------ 1 aron aron 2003248 2007-10-09 04:56 P1000061.JPG
-rwx------ 1 aron aron 1824310 2007-10-09 04:57 P1000063.JPG
-rwx------ 1 aron aron 1170500 2007-10-09 04:58 P1000065.JPG
-rwx------ 1 aron aron 1310977 2007-10-09 04:58 P1000066.JPG
-rwx------ 1 aron aron 1334350 2007-10-09 13:54 P1000068.JPG
-rwx------ 1 aron aron 1410103 2007-10-09 14:56 P1000076.JPG
-rwx------ 1 aron aron 1606759 2007-10-09 15:56 P1000089.JPG
-rwx------ 1 aron aron 1029105 2007-10-09 15:58 P1000096.JPG
-rwx------ 1 aron aron 1200386 2007-10-09 15:59 P1000097.JPG
-rwx------ 1 aron aron 1848100 2007-10-09 16:00 P1000100.JPG
-rwx------ 1 aron aron 2280168 2007-10-09 17:05 P1000103.JPG
-rwx------ 1 aron aron 1567744 2007-10-10 06:56 P1000109.JPG
-rwx------ 1 aron aron 1817052 2007-10-10 07:15 P1000110.JPG
-rwx------ 1 aron aron 1779885 2007-10-10 07:18 P1000111.JPG
-rwx------ 1 aron aron 1779427 2007-10-10 07:19 P1000112.JPG
-rwx------ 1 aron aron 1772441 2007-10-10 07:19 P1000113.JPG
-rwx------ 1 aron aron 1832746 2007-10-10 07:19 P1000114.JPG
-rwx------ 1 aron aron 1875004 2007-10-10 07:23 P1000115.JPG
-rwx------ 1 aron aron 1816462 2007-10-10 07:33 P1000117.JPG
-rwx------ 1 aron aron 1334422 2007-10-10 11:54 P1000118.JPG
-rwx------ 1 aron aron 1614521 2007-10-10 11:54 P1000119.JPG
-rwx------ 1 aron aron 2184617 2007-10-10 11:55 P1000122.JPG
-rwx------ 1 aron aron 2064473 2007-10-10 11:56 P1000124.JPG
-rwx------ 1 aron aron 2090744 2007-10-10 11:56 P1000125.JPG
-rwx------ 1 aron aron 2216131 2007-10-10 11:57 P1000128.JPG
-rwx------ 1 aron aron 2109952 2007-10-10 11:59 P1000130.JPG
-rwx------ 1 aron aron 2335510 2007-10-10 11:59 P1000132.JPG
-rwx------ 1 aron aron 1473947 2007-10-10 12:28 P1000133.JPG
-rwx------ 1 aron aron 1381894 2007-10-10 12:28 P1000134.JPG
-rwx------ 1 aron aron 1913754 2007-10-10 12:28 P1000135.JPG
-rwx------ 1 aron aron 1982113 2007-10-10 12:51 P1000137.JPG
-rwx------ 1 aron aron 1762013 2007-10-10 12:51 P1000140.JPG
-rwx------ 1 aron aron 2112137 2007-10-10 14:54 P1000143.JPG
-rwx------ 1 aron aron 1946287 2007-10-10 14:54 P1000145.JPG
-rwx------ 1 aron aron 2529278 2007-10-11 04:34 P1000152.JPG
-rwx------ 1 aron aron 2313279 2007-10-11 04:34 P1000153.JPG
-rwx------ 1 aron aron 2552752 2007-10-11 04:34 P1000154.JPG
-rwx------ 1 aron aron 2465198 2007-10-11 04:35 P1000155.JPG
-rwx------ 1 aron aron 2021352 2007-10-11 04:35 P1000156.JPG
-rwx------ 1 aron aron 2224303 2007-10-11 04:35 P1000157.JPG
-rwx------ 1 aron aron 2503971 2007-10-11 05:20 P1000158.JPG
-rwx------ 1 aron aron 2158459 2007-10-11 05:20 P1000159.JPG
-rwx------ 1 aron aron   89948 2007-10-11 05:26 P1000160.JPG
-rwx------ 1 aron aron   94279 2007-10-11 06:07 P1000162.JPG
-rwx------ 1 aron aron   31858 2007-10-11 06:08 P1000163.JPG
-rwx------ 1 aron aron 2478452 2007-10-11 08:55 P1000165.JPG
-rwx------ 1 aron aron   31449 2007-10-11 10:54 P1000167.JPG
-rwx------ 1 aron aron 1730655 2007-10-11 12:36 P1000176.JPG
-rwx------ 1 aron aron 1789407 2007-10-11 12:36 P1000177.JPG
-rwx------ 1 aron aron 2458898 2007-10-11 12:51 P1000179.JPG
-rwx------ 1 aron aron 1096595 2007-10-11 16:56 P1000186.JPG
-rwx------ 1 aron aron  780019 2007-10-11 16:56 P1000187.JPG
-rwx------ 1 aron aron 1564968 2007-10-11 16:57 P1000188.JPG
-rwx------ 1 aron aron  902196 2007-10-11 16:58 P1000189.JPG
-rwx------ 1 aron aron 1325612 2007-10-11 17:06 P1000192.JPG
-rwx------ 1 aron aron  989377 2007-10-11 17:07 P1000195.JPG
-rwx------ 1 aron aron 1540939 2007-10-11 17:07 P1000197.JPG
-rwx------ 1 aron aron  928325 2007-10-11 17:14 P1000198.JPG
-rwx------ 1 aron aron 1142360 2007-10-11 17:14 P1000200.JPG
-rwx------ 1 aron aron 1076744 2007-10-11 17:14 P1000201.JPG
-rwx------ 1 aron aron 1183587 2007-10-11 17:16 P1000202.JPG
-rwx------ 1 aron aron 1113438 2007-10-11 17:16 P1000204.JPG
-rwx------ 1 aron aron 1285703 2007-10-11 17:51 P1000205.JPG
-rwx------ 1 aron aron 1227200 2007-10-11 17:52 P1000206.JPG
-rwx------ 1 aron aron 1123264 2007-10-11 17:52 P1000207.JPG
-rwx------ 1 aron aron 1158193 2007-10-11 17:52 P1000208.JPG
-rwx------ 1 aron aron  875907 2007-10-11 17:53 P1000209.JPG
-rwx------ 1 aron aron 1030348 2007-10-11 17:54 P1000212.JPG
-rwx------ 1 aron aron 2104202 2007-10-12 05:42 P1000215.JPG
-rwx------ 1 aron aron 1190055 2007-10-12 05:42 P1000216.JPG
-rwx------ 1 aron aron  728704 2007-10-12 05:55 P1000217.JPG
-rwx------ 1 aron aron 1957488 2007-10-12 08:25 P1000219.JPG
-rwx------ 1 aron aron 2126347 2007-10-12 08:25 P1000220.JPG
-rwx------ 1 aron aron 1890614 2007-10-12 10:48 P1000228.JPG
-rwx------ 1 aron aron 1977518 2007-10-12 11:00 P1000230.JPG
-rwx------ 1 aron aron 2264835 2007-10-12 13:18 P1000231.JPG
-rwx------ 1 aron aron 2227757 2007-10-12 13:18 P1000232.JPG
-rwx------ 1 aron aron   31806 2007-10-13 06:00 P1000233.JPG
-rwx------ 1 aron aron   31822 2007-10-13 06:06 P1000235.JPG
-rwx------ 1 aron aron 1597969 2007-10-14 13:43 P1000236.JPG
-rwx------ 1 aron aron 2461283 2007-10-14 05:31 P1000237.JPG
-rwx------ 1 aron aron 1739697 2007-10-14 05:32 P1000239.JPG
-rwx------ 1 aron aron 2465510 2007-10-14 05:32 P1000240.JPG
-rwx------ 1 aron aron 1919775 2007-10-14 05:33 P1000242.JPG
-rwx------ 1 aron aron 2282356 2007-10-14 06:28 P1000243.JPG
-rwx------ 1 aron aron 2464970 2007-10-14 06:28 P1000244.JPG
-rwx------ 1 aron aron 1574947 2007-10-14 06:28 P1000246.JPG
-rwx------ 1 aron aron 1421225 2007-10-14 06:29 P1000248.JPG
-rwx------ 1 aron aron 1286378 2007-10-14 06:29 P1000249.JPG
-rwx------ 1 aron aron 2591597 2007-10-14 06:29 P1000250.JPG
-rwx------ 1 aron aron 2400101 2007-10-14 07:34 P1000252.JPG
-rwx------ 1 aron aron 1691437 2007-10-14 07:34 P1000255.JPG
-rwx------ 1 aron aron 1843105 2007-10-14 07:36 P1000261.JPG
-rwx------ 1 aron aron 1879270 2007-10-14 07:36 P1000262.JPG
-rwx------ 1 aron aron 1885254 2007-10-14 08:11 P1000264.JPG
-rwx------ 1 aron aron 2389165 2007-10-14 08:11 P1000265.JPG
-rwx------ 1 aron aron  423025 2007-10-14 15:13 P1000267.JPG
-rwx------ 1 aron aron 2175938 2007-10-14 08:50 P1000270.JPG
-rwx------ 1 aron aron 2190186 2007-10-14 08:58 P1000272.JPG
-rwx------ 1 aron aron 1483006 2007-10-14 09:00 P1000277.JPG
-rwx------ 1 aron aron 2554177 2007-10-14 09:02 P1000278.JPG
-rwx------ 1 aron aron 2563903 2007-10-14 09:08 P1000279.JPG
-rwx------ 1 aron aron 2475565 2007-10-14 09:10 P1000281.JPG
-rwx------ 1 aron aron 1618748 2007-10-14 09:15 P1000282.JPG
-rwx------ 1 aron aron 1862898 2007-10-14 09:30 P1000284.JPG
-rwx------ 1 aron aron 2272333 2007-10-14 09:34 P1000286.JPG
-rwx------ 1 aron aron 2314102 2007-10-14 09:35 P1000287.JPG
-rwx------ 1 aron aron 1790410 2007-10-14 09:36 P1000290.JPG
-rwx------ 1 aron aron 1709889 2007-10-14 09:37 P1000291.JPG
-rwx------ 1 aron aron 1912617 2007-10-14 09:45 P1000293.JPG
-rwx------ 1 aron aron 2180706 2007-10-14 12:53 P1000296.JPG
-rwx------ 1 aron aron 2376771 2007-10-14 13:36 P1000299.JPG
-rwx------ 1 aron aron 1974770 2007-10-15 02:39 P1000315.JPG
-rwx------ 1 aron aron 2136030 2007-10-15 02:40 P1000318.JPG
-rwx------ 1 aron aron 2479841 2007-10-15 06:00 P1000319.JPG
-rwx------ 1 aron aron 1875403 2007-10-15 07:18 P1000326.JPG
-rwx------ 1 aron aron 1817695 2007-10-15 07:18 P1000327.JPG
-rwx------ 1 aron aron 2468261 2007-10-15 07:19 P1000328.JPG
-rwx------ 1 aron aron 1148115 2007-10-15 07:20 P1000330.JPG
-rwx------ 1 aron aron 2091008 2007-10-15 07:22 P1000331.JPG
-rwx------ 1 aron aron 2461436 2007-10-15 07:23 P1000334.JPG
-rwx------ 1 aron aron 1658231 2007-10-15 07:24 P1000336.JPG
-rwx------ 1 aron aron 1761119 2007-10-15 07:26 P1000337.JPG
-rwx------ 1 aron aron 1971436 2007-10-15 07:29 P1000338.JPG
-rwx------ 1 aron aron 1789204 2007-10-15 07:30 P1000339.JPG
-rwx------ 1 aron aron 1767497 2007-10-15 07:30 P1000340.JPG
-rwx------ 1 aron aron 1692144 2007-10-15 07:33 P1000342.JPG
-rwx------ 1 aron aron 2330105 2007-10-15 07:33 P1000343.JPG
-rwx------ 1 aron aron 2484350 2007-10-15 07:33 P1000344.JPG
-rwx------ 1 aron aron 1568795 2007-10-15 11:31 P1000348.JPG
-rwx------ 1 aron aron 1289542 2007-10-15 11:32 P1000350.JPG
-rwx------ 1 aron aron  866390 2007-10-15 11:47 P1000351.JPG
-rwx------ 1 aron aron 1469089 2007-10-21 07:10 P1000434.JPG
-rwx------ 1 aron aron 2481200 2007-10-21 13:39 P1000439.JPG
-rwx------ 1 aron aron 1947206 2007-10-21 13:49 P1000452.JPG
-rwx------ 1 aron aron 2529012 2007-10-21 13:50 P1000453.JPG
-rwx------ 1 aron aron 2477337 2007-10-21 13:51 P1000454.JPG
-rwx------ 1 aron aron 2007141 2007-10-21 13:53 P1000457.JPG
-rwx------ 1 aron aron 1932788 2007-10-21 13:53 P1000458.JPG
-rwx------ 1 aron aron 1896213 2007-10-21 13:53 P1000459.JPG
-rwx------ 1 aron aron 1841600 2007-10-21 13:53 P1000460.JPG
-rwx------ 1 aron aron 1966775 2007-10-21 13:54 P1000461.JPG
-rwx------ 1 aron aron 1266307 2007-10-21 15:00 P1000484.JPG
-rwx------ 1 aron aron 1900782 2007-10-22 11:41 P1000494.JPG
-rwx------ 1 aron aron 1404436 2007-10-22 11:45 P1000508.JPG
-rwx------ 1 aron aron 1891682 2007-10-22 11:45 P1000510.JPG
-rwx------ 1 aron aron  985535 2007-10-22 11:47 P1000511.JPG
-rwx------ 1 aron aron 1763573 2007-10-22 11:47 P1000512.JPG
-rwx------ 1 aron aron 1555951 2007-10-22 11:48 P1000515.JPG
-rwx------ 1 aron aron 1664138 2007-10-22 11:48 P1000516.JPG
-rwx------ 1 aron aron 1838570 2007-10-22 11:50 P1000520.JPG
-rwx------ 1 aron aron 1831883 2007-10-22 11:51 P1000523.JPG
-rwx------ 1 aron aron 1287532 2007-10-22 11:52 P1000526.JPG
-rwx------ 1 aron aron 1609028 2007-10-22 11:53 P1000527.JPG
-rwx------ 1 aron aron 1490080 2007-10-22 11:56 P1000532.JPG
-rwx------ 1 aron aron 1293616 2007-10-22 11:59 P1000537.JPG
-rwx------ 1 aron aron 1172950 2007-10-22 13:04 P1000539.JPG
-rwx------ 1 aron aron 1937725 2007-10-22 12:10 P1000541.JPG
-rwx------ 1 aron aron 1412391 2007-10-22 13:03 P1000543.JPG
-rwx------ 1 aron aron 1642141 2007-10-22 12:13 P1000551.JPG
-rwx------ 1 aron aron 1549981 2007-10-22 12:15 P1000554.JPG
-rwx------ 1 aron aron 1191097 2007-10-22 12:16 P1000559.JPG
-rwx------ 1 aron aron 1850815 2007-10-22 12:18 P1000562.JPG
-rwx------ 1 aron aron 1691680 2007-10-22 12:20 P1000565.JPG
-rwx------ 1 aron aron 1346958 2007-10-22 12:22 P1000568.JPG
-rwx------ 1 aron aron 1510997 2007-10-22 12:23 P1000569.JPG
-rwx------ 1 aron aron 1556017 2007-10-22 12:23 P1000570.JPG
-rwx------ 1 aron aron 1368671 2007-10-22 12:23 P1000571.JPG
-rwx------ 1 aron aron  981274 2007-10-22 12:23 P1000572.JPG
-rwx------ 1 aron aron 1215831 2007-10-22 12:24 P1000573.JPG
-rwx------ 1 aron aron  512650 2007-10-22 12:24 P1000574.JPG
-rwx------ 1 aron aron 1325504 2007-10-22 12:24 P1000575.JPG
-rwx------ 1 aron aron 1150130 2007-10-22 12:25 P1000578.JPG
-rwx------ 1 aron aron 1635658 2007-10-22 12:27 P1000580.JPG
-rwx------ 1 aron aron 1641738 2007-10-22 12:27 P1000582.JPG
-rwx------ 1 aron aron 1145379 2007-10-22 12:28 P1000583.JPG
-rwx------ 1 aron aron 1716935 2007-10-22 13:10 P1000591.JPG
-rwx------ 1 aron aron 1797382 2007-10-22 13:33 P1000598.JPG
-rwx------ 1 aron aron 1835354 2007-10-22 13:39 P1000604.JPG
-rwx------ 1 aron aron 1590974 2007-10-22 13:40 P1000606.JPG
-rwx------ 1 aron aron 1525575 2007-10-22 13:40 P1000607.JPG
-rwx------ 1 aron aron 1227356 2007-10-22 13:41 P1000608.JPG
-rwx------ 1 aron aron  895823 2007-10-22 13:41 P1000609.JPG
-rwx------ 1 aron aron 1635347 2007-10-22 13:41 P1000610.JPG
-rwx------ 1 aron aron 1932476 2007-10-22 13:41 P1000611.JPG
-rwx------ 1 aron aron 1876795 2007-10-22 13:43 P1000613.JPG
-rwx------ 1 aron aron 1150438 2007-10-22 13:45 P1000617.JPG
-rwx------ 1 aron aron 1733591 2007-10-22 13:44 P1000619.JPG
-rwx------ 1 aron aron 1891137 2007-10-22 13:46 P1000621.JPG
-rwx------ 1 aron aron 1899682 2007-10-22 13:50 P1000625.JPG
-rwx------ 1 aron aron 1883446 2007-10-22 13:50 P1000627.JPG
-rwx------ 1 aron aron 1846380 2007-10-22 13:51 P1000629.JPG
-rwx------ 1 aron aron  501598 2007-10-22 13:51 P1000630.JPG
-rwx------ 1 aron aron 2010623 2007-10-22 13:52 P1000631.JPG
-rwx------ 1 aron aron 2026367 2007-10-22 14:27 P1000632.JPG
-rwx------ 1 aron aron 1647288 2007-10-22 14:31 P1000637.JPG
-rwx------ 1 aron aron 1377816 2007-10-22 14:34 P1000644.JPG
-rwx------ 1 aron aron 1337213 2007-10-22 14:34 P1000645.JPG
-rwx------ 1 aron aron 1198761 2007-10-22 14:35 P1000650.JPG
-rwx------ 1 aron aron 1418123 2007-10-22 14:36 P1000651.JPG
-rwx------ 1 aron aron 1973792 2007-10-22 14:38 P1000654.JPG
-rwx------ 1 aron aron 1869798 2007-10-22 14:38 P1000655.JPG
-rwx------ 1 aron aron 1427954 2007-10-22 16:12 P1000669.JPG
-rwx------ 1 aron aron 1140155 2007-10-22 16:13 P1000670.JPG
-rwx------ 1 aron aron 1341539 2007-10-22 16:14 P1000671.JPG
-rwx------ 1 aron aron 1235558 2007-10-22 16:17 P1000674.JPG
-rwx------ 1 aron aron 1183858 2007-10-22 16:17 P1000675.JPG
-rwx------ 1 aron aron 1430712 2007-10-22 16:20 P1000677.JPG
-rwx------ 1 aron aron 1447517 2007-10-22 16:20 P1000678.JPG
-rw-r--r-- 1 aron aron   19997 2007-10-23 15:26 proba.png
-rw-r--r-- 1 aron aron    3371 2007-10-04 15:52 reszletek.aup
drwxrwxr-x 2 aron aron    4096 2007-10-04 15:52 reszletek_data
drwxr-xr-x 3 aron aron    4096 2007-10-23 10:41 Unknown Artist
drwxr-xr-x 4 aron aron    4096 2007-10-05 15:26 Various
drwxr-xr-x 2 aron aron    4096 2007-10-23 16:26 video

```

rather long, i know but i was not sure what you would be able to use and what was just fodder to you.

thanks

robi

---

### Post by p_quarles on 2007-10-24
All right, his folder is in the correct place, so here's how you can setup the permissions for full access.

First, create a group (I'm using "family," here, but it can be anything you want):
```
sudo groupadd family
```
Add yourself to this group:
```
sudo addgroup *your-username* family
```
Change the group ownership of aron's folder:
```
sudo chgrp -R /home/aron
```
And set permissions to allow members of the group to have full access to this folder:
```
sudo chmod -R 774 /home/aron
```
For any other user folder you want access to, just repeat the last two steps replacing the username.

---

### Post by beanco on 2007-10-24
cool goings.. i will keep doing it but I got stuck

here

```
rob@rob-desktop:~$ sudo chgrp -R /home/aron
chgrp: missing operand after `/home/aron'
Try `chgrp --help' for more information.
rob@rob-desktop:~$ 

```


if I only new what operand is I might be able to figure out what one is missing.

robi

---

### Post by evilregis on 2007-10-24
I believe it should have been:

sudo chgrp -R family /home/aron

---

### Post by beanco on 2007-10-24
so i have set up the group family... i could chagne that at any time with now adverse affects, right?


by putting aron in the group family, and making the changes I and Aron have full access to /home/aron, right?

and aron has no access to /home/rob, right?

if I wanted to give him access to that I could do so, but how could I give him permission to view certain files and not others?

this stuff is actually fun!

thanks

robi

---

### Post by p_quarles on 2007-10-24
> **beanco said:**
> cool goings.. i will keep doing it but I got stuck

here

```
rob@rob-desktop:~$ sudo chgrp -R /home/aron
chgrp: missing operand after `/home/aron'
Try `chgrp --help' for more information.
rob@rob-desktop:~$ 

```
if I only new what operand is I might be able to figure out what one is missing.

robi
Apparently I need coffee. I gave you another bad command. [smacks self awake]

Replace that with this:
```
sudo chgrp -R family /home/aron
```

[EDIT]: Evilregis beat me to it.

In answer to the other question, I don't believe that changing the group ownership of Aron's folder would actually add him to that group. To check, though, you can type
```
cat /etc/group
```
Post the results here if you need help interpreting them. [/EDIT]

---

### Post by Inxsible on 2007-10-24
> **beanco said:**
> cool goings.. i will keep doing it but I got stuck

here

```
rob@rob-desktop:~$ sudo chgrp -R /home/aron
chgrp: missing operand after `/home/aron'
Try `chgrp --help' for more information.
rob@rob-desktop:~$ 

```if I only new what operand is I might be able to figure out what one is missing.

robi

if you get stuck on any command you could do this on the terminal:
```
 man *command-name*
```This will give you the entire manual (man) for that command and will help you in understanding what it does and how it is supposed to be used.

I use it all the time.

---

### Post by beanco on 2007-10-24
made the changes, thanks both of you.

i just went into midnight commander and wanted to access sg in /home/aron but i got this msg

```
cannot change directory
```

I can still change directories to other users... have I done sg wrong?

robi

edited to add:

in nautilus file browser i get into /home/aron, sort of...but i cannot access the files
> 

attempt to login failed

---

### Post by beanco on 2007-10-24
well i need help , I go thtis
```

rob@rob-desktop:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:rob,evi,aron,ancsi
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,rob,evi,aron,ancsi
fax:x:21:evi,aron,rob,ancsi
voice:x:22:
cdrom:x:24:haldaemon,rob,evi,aron,ancsi
floppy:x:25:haldaemon,rob,evi,aron,ancsi
tape:x:26:evi,aron,rob,ancsi
sudo:x:27:
audio:x:29:rob,evi,aron,ancsi
dip:x:30:rob,evi,aron,ancsi
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:rob
sasl:x:45:
plugdev:x:46:haldaemon,rob,evi,aron,ancsi
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:cupsys,hplip,rob,evi,aron,ancsi
nvram:x:105:
messagebus:x:106:
ssl-cert:x:107:cupsys
crontab:x:108:
ssh:x:109:
avahi-autoipd:x:110:
avahi:x:111:
netdev:x:112:rob
lpadmin:x:113:rob
haldaemon:x:114:
powerdev:x:115:haldaemon,rob
slocate:x:116:
admin:x:117:rob
gdm:x:118:
fuse:x:119:evi,aron,rob,ancsi
rob:x:1000:rob
aron:x:1004:rob
evi:x:1006:rob
test:x:1007:
ancsi:x:1001:ancsi,rob
family:x:1008:rob
```

as to using the man command I have tried that and I never really understand what it says... but I will try it more often, sooner or later I will get it.

robi

---

### Post by p_quarles on 2007-10-24
Did you run the corrected version of the chgrp command? Do that, and then run
```
sudo chmod -R 774 /home/aron
```
again.

---

### Post by beanco on 2007-10-24
did it and got this

```
rob@rob-desktop:/home/evi$ cd /home/aron
bash: cd: /home/aron: Permission denied
rob@rob-desktop:/home/evi$ 
```


in MC got the same old error msg.

in nautilus, same old error msg.

what i mess up?

how could I just delete the whole group and start over?

I assume delgroup or sg like that would work, and I also assume it will not harm the users or their files.

robi

---

### Post by p_quarles on 2007-10-24
I think you might need to log out and then back in before the permissions changes to your user take effect. Just to make sure it's working, though, let's see the output of this again:
```
ls -l /home/aron
```

---

### Post by beanco on 2007-10-24
What is this

```
rob@rob-desktop:~$ ls -l /home/aron
total 0
?--------- ? ? ? ?                ? /home/aron/180 ollie.JPG
?--------- ? ? ? ?                ? /home/aron/BEAT.aup
?--------- ? ? ? ?                ? /home/aron/BEAT.aup~
?--------- ? ? ? ?                ? /home/aron/BEAT_data
?--------- ? ? ? ?                ? /home/aron/cgmkhfhf
?--------- ? ? ? ?                ? /home/aron/chiicken.jpg
?--------- ? ? ? ?                ? /home/aron/cinemabox.jpg
?--------- ? ? ? ?                ? /home/aron/Desktop
?--------- ? ? ? ?                ? /home/aron/drum drum.wav
?--------- ? ? ? ?                ? /home/aron/drum.wav
?--------- ? ? ? ?                ? /home/aron/Examples
?--------- ? ? ? ?                ? /home/aron/fykyukyt
?--------- ? ? ? ?                ? /home/aron/gggtth
?--------- ? ? ? ?                ? /home/aron/home made music.aup
?--------- ? ? ? ?                ? /home/aron/MUUSIC
?--------- ? ? ? ?                ? /home/aron/nautilus-debug-log.txt
?--------- ? ? ? ?                ? /home/aron/P1000042.JPG
?--------- ? ? ? ?                ? /home/aron/P1000046.JPG
?--------- ? ? ? ?                ? /home/aron/P1000049.JPG
?--------- ? ? ? ?                ? /home/aron/P1000050.JPG
?--------- ? ? ? ?                ? /home/aron/P1000052.JPG
?--------- ? ? ? ?                ? /home/aron/P1000056.JPG
?--------- ? ? ? ?                ? /home/aron/P1000057.JPG
?--------- ? ? ? ?                ? /home/aron/P1000061.JPG
?--------- ? ? ? ?                ? /home/aron/P1000063.JPG
?--------- ? ? ? ?                ? /home/aron/P1000065.JPG
?--------- ? ? ? ?                ? /home/aron/P1000066.JPG
?--------- ? ? ? ?                ? /home/aron/P1000068.JPG
?--------- ? ? ? ?                ? /home/aron/P1000076.JPG
?--------- ? ? ? ?                ? /home/aron/P1000089.JPG
?--------- ? ? ? ?                ? /home/aron/P1000096.JPG
?--------- ? ? ? ?                ? /home/aron/P1000097.JPG
?--------- ? ? ? ?                ? /home/aron/P1000100.JPG
?--------- ? ? ? ?                ? /home/aron/P1000103.JPG
?--------- ? ? ? ?                ? /home/aron/P1000109.JPG
?--------- ? ? ? ?                ? /home/aron/P1000110.JPG
?--------- ? ? ? ?                ? /home/aron/P1000111.JPG
?--------- ? ? ? ?                ? /home/aron/P1000112.JPG
?--------- ? ? ? ?                ? /home/aron/P1000113.JPG
?--------- ? ? ? ?                ? /home/aron/P1000114.JPG
?--------- ? ? ? ?                ? /home/aron/P1000115.JPG
?--------- ? ? ? ?                ? /home/aron/P1000117.JPG
?--------- ? ? ? ?                ? /home/aron/P1000118.JPG
?--------- ? ? ? ?                ? /home/aron/P1000119.JPG
?--------- ? ? ? ?                ? /home/aron/P1000122.JPG
?--------- ? ? ? ?                ? /home/aron/P1000124.JPG
?--------- ? ? ? ?                ? /home/aron/P1000125.JPG
?--------- ? ? ? ?                ? /home/aron/P1000128.JPG
?--------- ? ? ? ?                ? /home/aron/P1000130.JPG
?--------- ? ? ? ?                ? /home/aron/P1000132.JPG
?--------- ? ? ? ?                ? /home/aron/P1000133.JPG
?--------- ? ? ? ?                ? /home/aron/P1000134.JPG
?--------- ? ? ? ?                ? /home/aron/P1000135.JPG
?--------- ? ? ? ?                ? /home/aron/P1000137.JPG
?--------- ? ? ? ?                ? /home/aron/P1000140.JPG
?--------- ? ? ? ?                ? /home/aron/P1000143.JPG
?--------- ? ? ? ?                ? /home/aron/P1000145.JPG
?--------- ? ? ? ?                ? /home/aron/P1000152.JPG
?--------- ? ? ? ?                ? /home/aron/P1000153.JPG
?--------- ? ? ? ?                ? /home/aron/P1000154.JPG
?--------- ? ? ? ?                ? /home/aron/P1000155.JPG
?--------- ? ? ? ?                ? /home/aron/P1000156.JPG
?--------- ? ? ? ?                ? /home/aron/P1000157.JPG
?--------- ? ? ? ?                ? /home/aron/P1000158.JPG
?--------- ? ? ? ?                ? /home/aron/P1000159.JPG
?--------- ? ? ? ?                ? /home/aron/P1000160.JPG
?--------- ? ? ? ?                ? /home/aron/P1000162.JPG
?--------- ? ? ? ?                ? /home/aron/P1000163.JPG
?--------- ? ? ? ?                ? /home/aron/P1000165.JPG
?--------- ? ? ? ?                ? /home/aron/P1000167.JPG
?--------- ? ? ? ?                ? /home/aron/P1000176.JPG
?--------- ? ? ? ?                ? /home/aron/P1000177.JPG
?--------- ? ? ? ?                ? /home/aron/P1000179.JPG
?--------- ? ? ? ?                ? /home/aron/P1000186.JPG
?--------- ? ? ? ?                ? /home/aron/P1000187.JPG
?--------- ? ? ? ?                ? /home/aron/P1000188.JPG
?--------- ? ? ? ?                ? /home/aron/P1000189.JPG
?--------- ? ? ? ?                ? /home/aron/P1000192.JPG
?--------- ? ? ? ?                ? /home/aron/P1000195.JPG
?--------- ? ? ? ?                ? /home/aron/P1000197.JPG
?--------- ? ? ? ?                ? /home/aron/P1000198.JPG
?--------- ? ? ? ?                ? /home/aron/P1000200.JPG
?--------- ? ? ? ?                ? /home/aron/P1000201.JPG
?--------- ? ? ? ?                ? /home/aron/P1000202.JPG
?--------- ? ? ? ?                ? /home/aron/P1000204.JPG
?--------- ? ? ? ?                ? /home/aron/P1000205.JPG
?--------- ? ? ? ?                ? /home/aron/P1000206.JPG
?--------- ? ? ? ?                ? /home/aron/P1000207.JPG
?--------- ? ? ? ?                ? /home/aron/P1000208.JPG
?--------- ? ? ? ?                ? /home/aron/P1000209.JPG
?--------- ? ? ? ?                ? /home/aron/P1000212.JPG
?--------- ? ? ? ?                ? /home/aron/P1000215.JPG
?--------- ? ? ? ?                ? /home/aron/P1000216.JPG
?--------- ? ? ? ?                ? /home/aron/P1000217.JPG
?--------- ? ? ? ?                ? /home/aron/P1000219.JPG
?--------- ? ? ? ?                ? /home/aron/P1000220.JPG
?--------- ? ? ? ?                ? /home/aron/P1000228.JPG
?--------- ? ? ? ?                ? /home/aron/P1000230.JPG
?--------- ? ? ? ?                ? /home/aron/P1000231.JPG
?--------- ? ? ? ?                ? /home/aron/P1000232.JPG
?--------- ? ? ? ?                ? /home/aron/P1000233.JPG
?--------- ? ? ? ?                ? /home/aron/P1000235.JPG
?--------- ? ? ? ?                ? /home/aron/P1000236.JPG
?--------- ? ? ? ?                ? /home/aron/P1000237.JPG
?--------- ? ? ? ?                ? /home/aron/P1000239.JPG
?--------- ? ? ? ?                ? /home/aron/P1000240.JPG
?--------- ? ? ? ?                ? /home/aron/P1000242.JPG
?--------- ? ? ? ?                ? /home/aron/P1000243.JPG
?--------- ? ? ? ?                ? /home/aron/P1000244.JPG
?--------- ? ? ? ?                ? /home/aron/P1000246.JPG
?--------- ? ? ? ?                ? /home/aron/P1000248.JPG
?--------- ? ? ? ?                ? /home/aron/P1000249.JPG
?--------- ? ? ? ?                ? /home/aron/P1000250.JPG
?--------- ? ? ? ?                ? /home/aron/P1000252.JPG
?--------- ? ? ? ?                ? /home/aron/P1000255.JPG
?--------- ? ? ? ?                ? /home/aron/P1000261.JPG
?--------- ? ? ? ?                ? /home/aron/P1000262.JPG
?--------- ? ? ? ?                ? /home/aron/P1000264.JPG
?--------- ? ? ? ?                ? /home/aron/P1000265.JPG
?--------- ? ? ? ?                ? /home/aron/P1000267.JPG
?--------- ? ? ? ?                ? /home/aron/P1000270.JPG
?--------- ? ? ? ?                ? /home/aron/P1000272.JPG
?--------- ? ? ? ?                ? /home/aron/P1000277.JPG
?--------- ? ? ? ?                ? /home/aron/P1000278.JPG
?--------- ? ? ? ?                ? /home/aron/P1000279.JPG
?--------- ? ? ? ?                ? /home/aron/P1000281.JPG
?--------- ? ? ? ?                ? /home/aron/P1000282.JPG
?--------- ? ? ? ?                ? /home/aron/P1000284.JPG
?--------- ? ? ? ?                ? /home/aron/P1000286.JPG
?--------- ? ? ? ?                ? /home/aron/P1000287.JPG
?--------- ? ? ? ?                ? /home/aron/P1000290.JPG
?--------- ? ? ? ?                ? /home/aron/P1000291.JPG
?--------- ? ? ? ?                ? /home/aron/P1000293.JPG
?--------- ? ? ? ?                ? /home/aron/P1000296.JPG
?--------- ? ? ? ?                ? /home/aron/P1000299.JPG
?--------- ? ? ? ?                ? /home/aron/P1000315.JPG
?--------- ? ? ? ?                ? /home/aron/P1000318.JPG
?--------- ? ? ? ?                ? /home/aron/P1000319.JPG
?--------- ? ? ? ?                ? /home/aron/P1000326.JPG
?--------- ? ? ? ?                ? /home/aron/P1000327.JPG
?--------- ? ? ? ?                ? /home/aron/P1000328.JPG
?--------- ? ? ? ?                ? /home/aron/P1000330.JPG
?--------- ? ? ? ?                ? /home/aron/P1000331.JPG
?--------- ? ? ? ?                ? /home/aron/P1000334.JPG
?--------- ? ? ? ?                ? /home/aron/P1000336.JPG
?--------- ? ? ? ?                ? /home/aron/P1000337.JPG
?--------- ? ? ? ?                ? /home/aron/P1000338.JPG
?--------- ? ? ? ?                ? /home/aron/P1000339.JPG
?--------- ? ? ? ?                ? /home/aron/P1000340.JPG
?--------- ? ? ? ?                ? /home/aron/P1000342.JPG
?--------- ? ? ? ?                ? /home/aron/P1000343.JPG
?--------- ? ? ? ?                ? /home/aron/P1000344.JPG
?--------- ? ? ? ?                ? /home/aron/P1000348.JPG
?--------- ? ? ? ?                ? /home/aron/P1000350.JPG
?--------- ? ? ? ?                ? /home/aron/P1000351.JPG
?--------- ? ? ? ?                ? /home/aron/P1000434.JPG
?--------- ? ? ? ?                ? /home/aron/P1000439.JPG
?--------- ? ? ? ?                ? /home/aron/P1000452.JPG
?--------- ? ? ? ?                ? /home/aron/P1000453.JPG
?--------- ? ? ? ?                ? /home/aron/P1000454.JPG
?--------- ? ? ? ?                ? /home/aron/P1000457.JPG
?--------- ? ? ? ?                ? /home/aron/P1000458.JPG
?--------- ? ? ? ?                ? /home/aron/P1000459.JPG
?--------- ? ? ? ?                ? /home/aron/P1000460.JPG
?--------- ? ? ? ?                ? /home/aron/P1000461.JPG
?--------- ? ? ? ?                ? /home/aron/P1000484.JPG
?--------- ? ? ? ?                ? /home/aron/P1000494.JPG
?--------- ? ? ? ?                ? /home/aron/P1000508.JPG
?--------- ? ? ? ?                ? /home/aron/P1000510.JPG
?--------- ? ? ? ?                ? /home/aron/P1000511.JPG
?--------- ? ? ? ?                ? /home/aron/P1000512.JPG
?--------- ? ? ? ?                ? /home/aron/P1000515.JPG
?--------- ? ? ? ?                ? /home/aron/P1000516.JPG
?--------- ? ? ? ?                ? /home/aron/P1000520.JPG
?--------- ? ? ? ?                ? /home/aron/P1000523.JPG
?--------- ? ? ? ?                ? /home/aron/P1000526.JPG
?--------- ? ? ? ?                ? /home/aron/P1000527.JPG
?--------- ? ? ? ?                ? /home/aron/P1000532.JPG
?--------- ? ? ? ?                ? /home/aron/P1000537.JPG
?--------- ? ? ? ?                ? /home/aron/P1000539.JPG
?--------- ? ? ? ?                ? /home/aron/P1000541.JPG
?--------- ? ? ? ?                ? /home/aron/P1000543.JPG
?--------- ? ? ? ?                ? /home/aron/P1000551.JPG
?--------- ? ? ? ?                ? /home/aron/P1000554.JPG
?--------- ? ? ? ?                ? /home/aron/P1000559.JPG
?--------- ? ? ? ?                ? /home/aron/P1000562.JPG
?--------- ? ? ? ?                ? /home/aron/P1000565.JPG
?--------- ? ? ? ?                ? /home/aron/P1000568.JPG
?--------- ? ? ? ?                ? /home/aron/P1000569.JPG
?--------- ? ? ? ?                ? /home/aron/P1000570.JPG
?--------- ? ? ? ?                ? /home/aron/P1000571.JPG
?--------- ? ? ? ?                ? /home/aron/P1000572.JPG
?--------- ? ? ? ?                ? /home/aron/P1000573.JPG
?--------- ? ? ? ?                ? /home/aron/P1000574.JPG
?--------- ? ? ? ?                ? /home/aron/P1000575.JPG
?--------- ? ? ? ?                ? /home/aron/P1000578.JPG
?--------- ? ? ? ?                ? /home/aron/P1000580.JPG
?--------- ? ? ? ?                ? /home/aron/P1000582.JPG
?--------- ? ? ? ?                ? /home/aron/P1000583.JPG
?--------- ? ? ? ?                ? /home/aron/P1000591.JPG
?--------- ? ? ? ?                ? /home/aron/P1000598.JPG
?--------- ? ? ? ?                ? /home/aron/P1000604.JPG
?--------- ? ? ? ?                ? /home/aron/P1000606.JPG
?--------- ? ? ? ?                ? /home/aron/P1000607.JPG
?--------- ? ? ? ?                ? /home/aron/P1000608.JPG
?--------- ? ? ? ?                ? /home/aron/P1000609.JPG
?--------- ? ? ? ?                ? /home/aron/P1000610.JPG
?--------- ? ? ? ?                ? /home/aron/P1000611.JPG
?--------- ? ? ? ?                ? /home/aron/P1000613.JPG
?--------- ? ? ? ?                ? /home/aron/P1000617.JPG
?--------- ? ? ? ?                ? /home/aron/P1000619.JPG
?--------- ? ? ? ?                ? /home/aron/P1000621.JPG
?--------- ? ? ? ?                ? /home/aron/P1000625.JPG
?--------- ? ? ? ?                ? /home/aron/P1000627.JPG
?--------- ? ? ? ?                ? /home/aron/P1000629.JPG
?--------- ? ? ? ?                ? /home/aron/P1000630.JPG
?--------- ? ? ? ?                ? /home/aron/P1000631.JPG
?--------- ? ? ? ?                ? /home/aron/P1000632.JPG
?--------- ? ? ? ?                ? /home/aron/P1000637.JPG
?--------- ? ? ? ?                ? /home/aron/P1000644.JPG
?--------- ? ? ? ?                ? /home/aron/P1000645.JPG
?--------- ? ? ? ?                ? /home/aron/P1000650.JPG
?--------- ? ? ? ?                ? /home/aron/P1000651.JPG
?--------- ? ? ? ?                ? /home/aron/P1000654.JPG
?--------- ? ? ? ?                ? /home/aron/P1000655.JPG
?--------- ? ? ? ?                ? /home/aron/P1000669.JPG
?--------- ? ? ? ?                ? /home/aron/P1000670.JPG
?--------- ? ? ? ?                ? /home/aron/P1000671.JPG
?--------- ? ? ? ?                ? /home/aron/P1000674.JPG
?--------- ? ? ? ?                ? /home/aron/P1000675.JPG
?--------- ? ? ? ?                ? /home/aron/P1000677.JPG
?--------- ? ? ? ?                ? /home/aron/P1000678.JPG
?--------- ? ? ? ?                ? /home/aron/proba.png
?--------- ? ? ? ?                ? /home/aron/reszletek.aup
?--------- ? ? ? ?                ? /home/aron/reszletek_data
?--------- ? ? ? ?                ? /home/aron/Unknown Artist
?--------- ? ? ? ?                ? /home/aron/Various
?--------- ? ? ? ?                ? /home/aron/video

```

is this correct or have I messed up things drastically?

robi

---

### Post by p_quarles on 2007-10-24
Hmm. That shouldn't be. 

Try this:
```
sudo chown -R aron:family /home/aron
```then:
```
sudo chmod -R 774 /home/aron
```again. 

You haven't done anything to mess it up. The "chgrp" command apparently didn't want to work like I thought it would, but there's no irreparable harm done.

EDIT: Btw, just to explain the numbers that go with the chmod command: the first number represents the owner's permissions (7=all), the second represents group permissions, and the third represents "others" (4=read only)

---

### Post by beanco on 2007-10-24
got the same thing, all those question marks.

robi

---

### Post by p_quarles on 2007-10-24
Wow. This is getting kinda strange. I have done this successfully before, so I know this *should* work. 

First, what does this say?:
```
ls -l /home
```
And then, make sure that user aron still exists. You can get a list of all users (most will be automated services) by typing:
```
cat /etc/passwd
```

---

### Post by beanco on 2007-10-24
strange, or interesting?

OK, for you it is strange because itis not doing what you want. for me interesting because I have no idea what is going on but will eventually learn from the process

here's what I got
```

rob@rob-desktop:~$ ls -l /home
total 28
drwxr-xr-x 16 ancsi ancsi   4096 2007-10-24 18:07 ancsi
drwxr--r-- 34 aron  family 12288 2007-10-24 19:37 aron
drwxr-xr-x 12 evi   evi     4096 2007-10-14 16:40 evi
drwx------ 41 rob   rob     4096 2007-10-24 21:08 rob
drwxr-xr-x 12  1004 test    4096 2007-10-18 19:50 test
rob@rob-desktop:~$ 

```

and I assume it is the last few lines of the following that you need.

```
rob@rob-desktop:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:106::/var/run/dbus:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
cupsys:x:106:113::/home/cupsys:/bin/false
haldaemon:x:107:114:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
hplip:x:108:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:109:118:Gnome Display Manager:/var/lib/gdm:/bin/false
rob:x:1000:1000:rob,,,:/home/rob:/bin/bash
aron:x:1001:1004:aron,,,,:/home/aron:/bin/bash
evi:x:1003:1006:evi,,,,:/home/evi:/bin/bash
ancsi:x:1002:1001:anna rebecca dawson,2,282 6398,282 6398:/home/ancsi:/bin/bash
rob@rob-desktop:~$ cat /etc/passwd

```

it seems that I am not a member of the group family. is this the problem?

---

### Post by p_quarles on 2007-10-24
I *think* I see what happened. I initially typed "chmod 744." I edited it shortly thereafter to read correctly (chmod 774), but probably after you typed it in. 

The ownership is correct, and the permissions took effect, so run this again and then list the files:
```
sudo chmod -R 774 /home/aron
```EDIT: Another explanation: Directories need to be executable in order for them to open. chmod 744 made the the directory readable and writable, but not executable, to the group.

EDIT 2: Earlier when you ran "cat /etc/group," it showed that you were a member of the group "family." You can run that again if you're not sure. But basically, /etc/group lists groups and their members, and /etc/passwd lists users.

---

### Post by beanco on 2007-10-24
copied and pasted the 774 command...

then ran the ls -l /home/aron and got all the question marks again.

rob

---

### Post by p_quarles on 2007-10-24
All right. I'm not exactly sure how I got you into this mess, but I'll do my best to fix it. (as a side note, did you ever try logging out and back into your account? if not, try that before doing anything else).

Give this a try:
```
sudo -i
```
This will give you a root shell. Now, go to aron's home directory:
```
cd /home/aron
```
From within the directory, type the following:
```
chown -R aron:family *
chmod -R 774 *
```
You won't need to use "sudo" with these commands, since you are already in root. Now, check the directory again by typing
```
ls -l
```
Type "exit" to get out of root mode, and let me know what happened this time.

---

### Post by beanco on 2007-10-24
got this now

```
rob@rob-desktop:/home/aron$ ls -l
total 358692
-rwxrwxr-- 1 aron family       0 2007-10-23 14:15 180 ollie.JPG
-rwxrwxr-- 1 aron family    3616 2007-10-04 14:58 BEAT.aup
-rwxrwxr-- 1 aron family     885 2007-10-04 14:41 BEAT.aup~
drwxrwxr-- 2 aron family   20480 2007-10-04 15:02 BEAT_data
-rwxrwxr-- 1 aron family      96 2007-10-15 14:53 cgmkhfhf
-rwxrwxr-- 1 aron family  409044 2007-10-19 15:49 chiicken.jpg
-rwxrwxr-- 1 aron family  124462 2007-10-19 15:44 cinemabox.jpg
drwxrwxr-- 2 aron family    4096 2007-10-24 17:17 Desktop
-rwxrwxr-- 1 aron family 2031404 2007-10-05 15:25 drum drum.wav
-rwxrwxr-- 1 aron family 1397804 2007-10-05 15:24 drum.wav
lrwxrwxrwx 1 aron family      26 2007-10-02 18:10 Examples -> /usr/share/example-content
-rwxrwxr-- 1 aron family     269 2007-10-18 16:48 fykyukyt
drwxrwxr-- 2 aron family    4096 2007-10-19 16:42 gggtth
-rwxrwxr-- 1 aron family    3010 2007-10-03 18:24 home made music.aup
drwxrwxr-- 3 aron family    4096 2007-10-18 16:30 MUUSIC
-rwxrwxr-- 1 aron family   12334 2007-10-23 13:48 nautilus-debug-log.txt
-rwxrwxr-- 1 aron family 2257399 2007-10-09 01:19 P1000042.JPG
-rwxrwxr-- 1 aron family 1355578 2007-10-09 01:21 P1000046.JPG
-rwxrwxr-- 1 aron family 1988767 2007-10-09 01:23 P1000049.JPG
-rwxrwxr-- 1 aron family 2106562 2007-10-09 01:24 P1000050.JPG
-rwxrwxr-- 1 aron family 1821054 2007-10-09 02:53 P1000052.JPG
-rwxrwxr-- 1 aron family 1806730 2007-10-09 04:44 P1000056.JPG
-rwxrwxr-- 1 aron family 1856455 2007-10-09 04:44 P1000057.JPG
-rwxrwxr-- 1 aron family 2003248 2007-10-09 04:56 P1000061.JPG
-rwxrwxr-- 1 aron family 1824310 2007-10-09 04:57 P1000063.JPG
-rwxrwxr-- 1 aron family 1170500 2007-10-09 04:58 P1000065.JPG
-rwxrwxr-- 1 aron family 1310977 2007-10-09 04:58 P1000066.JPG
-rwxrwxr-- 1 aron family 1334350 2007-10-09 13:54 P1000068.JPG
-rwxrwxr-- 1 aron family 1410103 2007-10-09 14:56 P1000076.JPG
-rwxrwxr-- 1 aron family 1606759 2007-10-09 15:56 P1000089.JPG
-rwxrwxr-- 1 aron family 1029105 2007-10-09 15:58 P1000096.JPG
-rwxrwxr-- 1 aron family 1200386 2007-10-09 15:59 P1000097.JPG
-rwxrwxr-- 1 aron family 1848100 2007-10-09 16:00 P1000100.JPG
-rwxrwxr-- 1 aron family 2280168 2007-10-09 17:05 P1000103.JPG
-rwxrwxr-- 1 aron family 1567744 2007-10-10 06:56 P1000109.JPG
-rwxrwxr-- 1 aron family 1817052 2007-10-10 07:15 P1000110.JPG
-rwxrwxr-- 1 aron family 1779885 2007-10-10 07:18 P1000111.JPG
-rwxrwxr-- 1 aron family 1779427 2007-10-10 07:19 P1000112.JPG
-rwxrwxr-- 1 aron family 1772441 2007-10-10 07:19 P1000113.JPG
-rwxrwxr-- 1 aron family 1832746 2007-10-10 07:19 P1000114.JPG
-rwxrwxr-- 1 aron family 1875004 2007-10-10 07:23 P1000115.JPG
-rwxrwxr-- 1 aron family 1816462 2007-10-10 07:33 P1000117.JPG
-rwxrwxr-- 1 aron family 1334422 2007-10-10 11:54 P1000118.JPG
-rwxrwxr-- 1 aron family 1614521 2007-10-10 11:54 P1000119.JPG
-rwxrwxr-- 1 aron family 2184617 2007-10-10 11:55 P1000122.JPG
-rwxrwxr-- 1 aron family 2064473 2007-10-10 11:56 P1000124.JPG
-rwxrwxr-- 1 aron family 2090744 2007-10-10 11:56 P1000125.JPG
-rwxrwxr-- 1 aron family 2216131 2007-10-10 11:57 P1000128.JPG
-rwxrwxr-- 1 aron family 2109952 2007-10-10 11:59 P1000130.JPG
-rwxrwxr-- 1 aron family 2335510 2007-10-10 11:59 P1000132.JPG
-rwxrwxr-- 1 aron family 1473947 2007-10-10 12:28 P1000133.JPG
-rwxrwxr-- 1 aron family 1381894 2007-10-10 12:28 P1000134.JPG
-rwxrwxr-- 1 aron family 1913754 2007-10-10 12:28 P1000135.JPG
-rwxrwxr-- 1 aron family 1982113 2007-10-10 12:51 P1000137.JPG
-rwxrwxr-- 1 aron family 1762013 2007-10-10 12:51 P1000140.JPG
-rwxrwxr-- 1 aron family 2112137 2007-10-10 14:54 P1000143.JPG
-rwxrwxr-- 1 aron family 1946287 2007-10-10 14:54 P1000145.JPG
-rwxrwxr-- 1 aron family 2529278 2007-10-11 04:34 P1000152.JPG
-rwxrwxr-- 1 aron family 2313279 2007-10-11 04:34 P1000153.JPG
-rwxrwxr-- 1 aron family 2552752 2007-10-11 04:34 P1000154.JPG
-rwxrwxr-- 1 aron family 2465198 2007-10-11 04:35 P1000155.JPG
-rwxrwxr-- 1 aron family 2021352 2007-10-11 04:35 P1000156.JPG
-rwxrwxr-- 1 aron family 2224303 2007-10-11 04:35 P1000157.JPG
-rwxrwxr-- 1 aron family 2503971 2007-10-11 05:20 P1000158.JPG
-rwxrwxr-- 1 aron family 2158459 2007-10-11 05:20 P1000159.JPG
-rwxrwxr-- 1 aron family   89948 2007-10-11 05:26 P1000160.JPG
-rwxrwxr-- 1 aron family   94279 2007-10-11 06:07 P1000162.JPG
-rwxrwxr-- 1 aron family   31858 2007-10-11 06:08 P1000163.JPG
-rwxrwxr-- 1 aron family 2478452 2007-10-11 08:55 P1000165.JPG
-rwxrwxr-- 1 aron family   31449 2007-10-11 10:54 P1000167.JPG
-rwxrwxr-- 1 aron family 1730655 2007-10-11 12:36 P1000176.JPG
-rwxrwxr-- 1 aron family 1789407 2007-10-11 12:36 P1000177.JPG
-rwxrwxr-- 1 aron family 2458898 2007-10-11 12:51 P1000179.JPG
-rwxrwxr-- 1 aron family 1096595 2007-10-11 16:56 P1000186.JPG
-rwxrwxr-- 1 aron family  780019 2007-10-11 16:56 P1000187.JPG
-rwxrwxr-- 1 aron family 1564968 2007-10-11 16:57 P1000188.JPG
-rwxrwxr-- 1 aron family  902196 2007-10-11 16:58 P1000189.JPG
-rwxrwxr-- 1 aron family 1325612 2007-10-11 17:06 P1000192.JPG
-rwxrwxr-- 1 aron family  989377 2007-10-11 17:07 P1000195.JPG
-rwxrwxr-- 1 aron family 1540939 2007-10-11 17:07 P1000197.JPG
-rwxrwxr-- 1 aron family  928325 2007-10-11 17:14 P1000198.JPG
-rwxrwxr-- 1 aron family 1142360 2007-10-11 17:14 P1000200.JPG
-rwxrwxr-- 1 aron family 1076744 2007-10-11 17:14 P1000201.JPG
-rwxrwxr-- 1 aron family 1183587 2007-10-11 17:16 P1000202.JPG
-rwxrwxr-- 1 aron family 1113438 2007-10-11 17:16 P1000204.JPG
-rwxrwxr-- 1 aron family 1285703 2007-10-11 17:51 P1000205.JPG
-rwxrwxr-- 1 aron family 1227200 2007-10-11 17:52 P1000206.JPG
-rwxrwxr-- 1 aron family 1123264 2007-10-11 17:52 P1000207.JPG
-rwxrwxr-- 1 aron family 1158193 2007-10-11 17:52 P1000208.JPG
-rwxrwxr-- 1 aron family  875907 2007-10-11 17:53 P1000209.JPG
-rwxrwxr-- 1 aron family 1030348 2007-10-11 17:54 P1000212.JPG
-rwxrwxr-- 1 aron family 2104202 2007-10-12 05:42 P1000215.JPG
-rwxrwxr-- 1 aron family 1190055 2007-10-12 05:42 P1000216.JPG
-rwxrwxr-- 1 aron family  728704 2007-10-12 05:55 P1000217.JPG
-rwxrwxr-- 1 aron family 1957488 2007-10-12 08:25 P1000219.JPG
-rwxrwxr-- 1 aron family 2126347 2007-10-12 08:25 P1000220.JPG
-rwxrwxr-- 1 aron family 1890614 2007-10-12 10:48 P1000228.JPG
-rwxrwxr-- 1 aron family 1977518 2007-10-12 11:00 P1000230.JPG
-rwxrwxr-- 1 aron family 2264835 2007-10-12 13:18 P1000231.JPG
-rwxrwxr-- 1 aron family 2227757 2007-10-12 13:18 P1000232.JPG
-rwxrwxr-- 1 aron family   31806 2007-10-13 06:00 P1000233.JPG
-rwxrwxr-- 1 aron family   31822 2007-10-13 06:06 P1000235.JPG
-rwxrwxr-- 1 aron family 1597969 2007-10-14 13:43 P1000236.JPG
-rwxrwxr-- 1 aron family 2461283 2007-10-14 05:31 P1000237.JPG
-rwxrwxr-- 1 aron family 1739697 2007-10-14 05:32 P1000239.JPG
-rwxrwxr-- 1 aron family 2465510 2007-10-14 05:32 P1000240.JPG
-rwxrwxr-- 1 aron family 1919775 2007-10-14 05:33 P1000242.JPG
-rwxrwxr-- 1 aron family 2282356 2007-10-14 06:28 P1000243.JPG
-rwxrwxr-- 1 aron family 2464970 2007-10-14 06:28 P1000244.JPG
-rwxrwxr-- 1 aron family 1574947 2007-10-14 06:28 P1000246.JPG
-rwxrwxr-- 1 aron family 1421225 2007-10-14 06:29 P1000248.JPG
-rwxrwxr-- 1 aron family 1286378 2007-10-14 06:29 P1000249.JPG
-rwxrwxr-- 1 aron family 2591597 2007-10-14 06:29 P1000250.JPG
-rwxrwxr-- 1 aron family 2400101 2007-10-14 07:34 P1000252.JPG
-rwxrwxr-- 1 aron family 1691437 2007-10-14 07:34 P1000255.JPG
-rwxrwxr-- 1 aron family 1843105 2007-10-14 07:36 P1000261.JPG
-rwxrwxr-- 1 aron family 1879270 2007-10-14 07:36 P1000262.JPG
-rwxrwxr-- 1 aron family 1885254 2007-10-14 08:11 P1000264.JPG
-rwxrwxr-- 1 aron family 2389165 2007-10-14 08:11 P1000265.JPG
-rwxrwxr-- 1 aron family  423025 2007-10-14 15:13 P1000267.JPG
-rwxrwxr-- 1 aron family 2175938 2007-10-14 08:50 P1000270.JPG
-rwxrwxr-- 1 aron family 2190186 2007-10-14 08:58 P1000272.JPG
-rwxrwxr-- 1 aron family 1483006 2007-10-14 09:00 P1000277.JPG
-rwxrwxr-- 1 aron family 2554177 2007-10-14 09:02 P1000278.JPG
-rwxrwxr-- 1 aron family 2563903 2007-10-14 09:08 P1000279.JPG
-rwxrwxr-- 1 aron family 2475565 2007-10-14 09:10 P1000281.JPG
-rwxrwxr-- 1 aron family 1618748 2007-10-14 09:15 P1000282.JPG
-rwxrwxr-- 1 aron family 1862898 2007-10-14 09:30 P1000284.JPG
-rwxrwxr-- 1 aron family 2272333 2007-10-14 09:34 P1000286.JPG
-rwxrwxr-- 1 aron family 2314102 2007-10-14 09:35 P1000287.JPG
-rwxrwxr-- 1 aron family 1790410 2007-10-14 09:36 P1000290.JPG
-rwxrwxr-- 1 aron family 1709889 2007-10-14 09:37 P1000291.JPG
-rwxrwxr-- 1 aron family 1912617 2007-10-14 09:45 P1000293.JPG
-rwxrwxr-- 1 aron family 2180706 2007-10-14 12:53 P1000296.JPG
-rwxrwxr-- 1 aron family 2376771 2007-10-14 13:36 P1000299.JPG
-rwxrwxr-- 1 aron family 1974770 2007-10-15 02:39 P1000315.JPG
-rwxrwxr-- 1 aron family 2136030 2007-10-15 02:40 P1000318.JPG
-rwxrwxr-- 1 aron family 2479841 2007-10-15 06:00 P1000319.JPG
-rwxrwxr-- 1 aron family 1875403 2007-10-15 07:18 P1000326.JPG
-rwxrwxr-- 1 aron family 1817695 2007-10-15 07:18 P1000327.JPG
-rwxrwxr-- 1 aron family 2468261 2007-10-15 07:19 P1000328.JPG
-rwxrwxr-- 1 aron family 1148115 2007-10-15 07:20 P1000330.JPG
-rwxrwxr-- 1 aron family 2091008 2007-10-15 07:22 P1000331.JPG
-rwxrwxr-- 1 aron family 2461436 2007-10-15 07:23 P1000334.JPG
-rwxrwxr-- 1 aron family 1658231 2007-10-15 07:24 P1000336.JPG
-rwxrwxr-- 1 aron family 1761119 2007-10-15 07:26 P1000337.JPG
-rwxrwxr-- 1 aron family 1971436 2007-10-15 07:29 P1000338.JPG
-rwxrwxr-- 1 aron family 1789204 2007-10-15 07:30 P1000339.JPG
-rwxrwxr-- 1 aron family 1767497 2007-10-15 07:30 P1000340.JPG
-rwxrwxr-- 1 aron family 1692144 2007-10-15 07:33 P1000342.JPG
-rwxrwxr-- 1 aron family 2330105 2007-10-15 07:33 P1000343.JPG
-rwxrwxr-- 1 aron family 2484350 2007-10-15 07:33 P1000344.JPG
-rwxrwxr-- 1 aron family 1568795 2007-10-15 11:31 P1000348.JPG
-rwxrwxr-- 1 aron family 1289542 2007-10-15 11:32 P1000350.JPG
-rwxrwxr-- 1 aron family  866390 2007-10-15 11:47 P1000351.JPG
-rwxrwxr-- 1 aron family 1469089 2007-10-21 07:10 P1000434.JPG
-rwxrwxr-- 1 aron family 2481200 2007-10-21 13:39 P1000439.JPG
-rwxrwxr-- 1 aron family 1947206 2007-10-21 13:49 P1000452.JPG
-rwxrwxr-- 1 aron family 2529012 2007-10-21 13:50 P1000453.JPG
-rwxrwxr-- 1 aron family 2477337 2007-10-21 13:51 P1000454.JPG
-rwxrwxr-- 1 aron family 2007141 2007-10-21 13:53 P1000457.JPG
-rwxrwxr-- 1 aron family 1932788 2007-10-21 13:53 P1000458.JPG
-rwxrwxr-- 1 aron family 1896213 2007-10-21 13:53 P1000459.JPG
-rwxrwxr-- 1 aron family 1841600 2007-10-21 13:53 P1000460.JPG
-rwxrwxr-- 1 aron family 1966775 2007-10-21 13:54 P1000461.JPG
-rwxrwxr-- 1 aron family 1266307 2007-10-21 15:00 P1000484.JPG
-rwxrwxr-- 1 aron family 1900782 2007-10-22 11:41 P1000494.JPG
-rwxrwxr-- 1 aron family 1404436 2007-10-22 11:45 P1000508.JPG
-rwxrwxr-- 1 aron family 1891682 2007-10-22 11:45 P1000510.JPG
-rwxrwxr-- 1 aron family  985535 2007-10-22 11:47 P1000511.JPG
-rwxrwxr-- 1 aron family 1763573 2007-10-22 11:47 P1000512.JPG
-rwxrwxr-- 1 aron family 1555951 2007-10-22 11:48 P1000515.JPG
-rwxrwxr-- 1 aron family 1664138 2007-10-22 11:48 P1000516.JPG
-rwxrwxr-- 1 aron family 1838570 2007-10-22 11:50 P1000520.JPG
-rwxrwxr-- 1 aron family 1831883 2007-10-22 11:51 P1000523.JPG
-rwxrwxr-- 1 aron family 1287532 2007-10-22 11:52 P1000526.JPG
-rwxrwxr-- 1 aron family 1609028 2007-10-22 11:53 P1000527.JPG
-rwxrwxr-- 1 aron family 1490080 2007-10-22 11:56 P1000532.JPG
-rwxrwxr-- 1 aron family 1293616 2007-10-22 11:59 P1000537.JPG
-rwxrwxr-- 1 aron family 1172950 2007-10-22 13:04 P1000539.JPG
-rwxrwxr-- 1 aron family 1937725 2007-10-22 12:10 P1000541.JPG
-rwxrwxr-- 1 aron family 1412391 2007-10-22 13:03 P1000543.JPG
-rwxrwxr-- 1 aron family 1642141 2007-10-22 12:13 P1000551.JPG
-rwxrwxr-- 1 aron family 1549981 2007-10-22 12:15 P1000554.JPG
-rwxrwxr-- 1 aron family 1191097 2007-10-22 12:16 P1000559.JPG
-rwxrwxr-- 1 aron family 1850815 2007-10-22 12:18 P1000562.JPG
-rwxrwxr-- 1 aron family 1691680 2007-10-22 12:20 P1000565.JPG
-rwxrwxr-- 1 aron family 1346958 2007-10-22 12:22 P1000568.JPG
-rwxrwxr-- 1 aron family 1510997 2007-10-22 12:23 P1000569.JPG
-rwxrwxr-- 1 aron family 1556017 2007-10-22 12:23 P1000570.JPG
-rwxrwxr-- 1 aron family 1368671 2007-10-22 12:23 P1000571.JPG
-rwxrwxr-- 1 aron family  981274 2007-10-22 12:23 P1000572.JPG
-rwxrwxr-- 1 aron family 1215831 2007-10-22 12:24 P1000573.JPG
-rwxrwxr-- 1 aron family  512650 2007-10-22 12:24 P1000574.JPG
-rwxrwxr-- 1 aron family 1325504 2007-10-22 12:24 P1000575.JPG
-rwxrwxr-- 1 aron family 1150130 2007-10-22 12:25 P1000578.JPG
-rwxrwxr-- 1 aron family 1635658 2007-10-22 12:27 P1000580.JPG
-rwxrwxr-- 1 aron family 1641738 2007-10-22 12:27 P1000582.JPG
-rwxrwxr-- 1 aron family 1145379 2007-10-22 12:28 P1000583.JPG
-rwxrwxr-- 1 aron family 1716935 2007-10-22 13:10 P1000591.JPG
-rwxrwxr-- 1 aron family 1797382 2007-10-22 13:33 P1000598.JPG
-rwxrwxr-- 1 aron family 1835354 2007-10-22 13:39 P1000604.JPG
-rwxrwxr-- 1 aron family 1590974 2007-10-22 13:40 P1000606.JPG
-rwxrwxr-- 1 aron family 1525575 2007-10-22 13:40 P1000607.JPG
-rwxrwxr-- 1 aron family 1227356 2007-10-22 13:41 P1000608.JPG
-rwxrwxr-- 1 aron family  895823 2007-10-22 13:41 P1000609.JPG
-rwxrwxr-- 1 aron family 1635347 2007-10-22 13:41 P1000610.JPG
-rwxrwxr-- 1 aron family 1932476 2007-10-22 13:41 P1000611.JPG
-rwxrwxr-- 1 aron family 1876795 2007-10-22 13:43 P1000613.JPG
-rwxrwxr-- 1 aron family 1150438 2007-10-22 13:45 P1000617.JPG
-rwxrwxr-- 1 aron family 1733591 2007-10-22 13:44 P1000619.JPG
-rwxrwxr-- 1 aron family 1891137 2007-10-22 13:46 P1000621.JPG
-rwxrwxr-- 1 aron family 1899682 2007-10-22 13:50 P1000625.JPG
-rwxrwxr-- 1 aron family 1883446 2007-10-22 13:50 P1000627.JPG
-rwxrwxr-- 1 aron family 1846380 2007-10-22 13:51 P1000629.JPG
-rwxrwxr-- 1 aron family  501598 2007-10-22 13:51 P1000630.JPG
-rwxrwxr-- 1 aron family 2010623 2007-10-22 13:52 P1000631.JPG
-rwxrwxr-- 1 aron family 2026367 2007-10-22 14:27 P1000632.JPG
-rwxrwxr-- 1 aron family 1647288 2007-10-22 14:31 P1000637.JPG
-rwxrwxr-- 1 aron family 1377816 2007-10-22 14:34 P1000644.JPG
-rwxrwxr-- 1 aron family 1337213 2007-10-22 14:34 P1000645.JPG
-rwxrwxr-- 1 aron family 1198761 2007-10-22 14:35 P1000650.JPG
-rwxrwxr-- 1 aron family 1418123 2007-10-22 14:36 P1000651.JPG
-rwxrwxr-- 1 aron family 1973792 2007-10-22 14:38 P1000654.JPG
-rwxrwxr-- 1 aron family 1869798 2007-10-22 14:38 P1000655.JPG
-rwxrwxr-- 1 aron family 1427954 2007-10-22 16:12 P1000669.JPG
-rwxrwxr-- 1 aron family 1140155 2007-10-22 16:13 P1000670.JPG
-rwxrwxr-- 1 aron family 1341539 2007-10-22 16:14 P1000671.JPG
-rwxrwxr-- 1 aron family 1235558 2007-10-22 16:17 P1000674.JPG
-rwxrwxr-- 1 aron family 1183858 2007-10-22 16:17 P1000675.JPG
-rwxrwxr-- 1 aron family 1430712 2007-10-22 16:20 P1000677.JPG
-rwxrwxr-- 1 aron family 1447517 2007-10-22 16:20 P1000678.JPG
-rwxrwxr-- 1 aron family   19997 2007-10-23 15:26 proba.png
-rwxrwxr-- 1 aron family    3371 2007-10-04 15:52 reszletek.aup
drwxrwxr-- 2 aron family    4096 2007-10-04 15:52 reszletek_data
drwxrwxr-- 3 aron family    4096 2007-10-23 10:41 Unknown Artist
drwxrwxr-- 4 aron family    4096 2007-10-05 15:26 Various
drwxrwxr-- 2 aron family    4096 2007-10-23 16:26 video

```

sorry to cause you concern, confusion.

I think what had happened is that did not log out... i had to attend to sg here at home and when I got back I thought I had logotu already. now all I did was log out, log back in and got the above...

so if I do the same for the other users i will have access to their accounts too. great!

how do I let them have access, say reading only to certain files and not to entire groups?

thanks for all your help!!!
and again, sorry for causing so many problems.

robi

---

### Post by beanco on 2007-10-24
just logged as aron and got the dreaded   

homeuser/.dmrc is being ignored..... so forth and so on....

what up with that?


robi

---

### Post by p_quarles on 2007-10-24
To your first question, in retrospect I would say it's probably safer to change permissions this way:
login as the user whose permissions you want to change:
```
sudo su *username*
```
Then run the changes, this time using wildcards (this will avoid the problem with .dmrc)
```
chown -R *username*:family *
chmod -R 774 *
```
Then, exit to log out of that user's account. 

To fix aron's account, run this:
```
sudo chmod 600 /home/aron/.dmrc
```
That should set that file's permissions back to the default. 

Sorry that I led you a little bit astray. Like I said, I've done this before, but not with actual human users, just with system users that I would normally administer with root privileges. For human users, there are some extra things to account for that I wasn't thinking about. :(

Anyway, I'm pretty confident that these revised instructions will prevent these same issues from recurring, and that the second command will fix the issue with aron's account. Let me know, of course, if it doesn't.

---

### Post by beanco on 2007-10-26
I tried it all and I stll get the .dmrc error msg when I log on as aron.

thanks, though!


I was about to sit down and go thorugh the first set of command you gave me to figure otu how they work and then do the same thing to my daughter's account.

but now you send me the second one... so I will have to figure that out too...

robi

---

### Post by p_quarles on 2007-10-26
Okay, I looked into the .dmrc issue a little further, and found this post:
> **bodhi.zazen said:**
> Well I assume you somehow changed the permissions of your home directory

Must have been more then that if you are still getting an error, so :
```
sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown -R user_name /home/user_name
```                      

.drmc file permissions, in a terminal: (use first set)

    OR, if that fails:
```
 			 					sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc
```

Where  user_name = your log-in name :razz:

That's from [this]("http://ubuntuforums.org/showthread.php?t=565934&highlight=dmrc") thread. The user was experiencing a similar login error (only with his own account), and he says this fixed, though he doesn't say which of the two options fixed it.

The first one does essentially the same thing I told you to do. The fallback method simply deletes the current .dmrc file, on the premise that a new one will be generated automatically when the user logs back in. 

Now, you'll want to make some modifications to those commands, since bodhi.zazen is addressing a single user situation. In the "chown" commands, change *user_name *to *user_name*:family. That will set both the user and group that owns the directory. With the "chmod" commands, change the second numeral to 7 so that group users (i.e., you) have full permissions. The last one can be 4 or 5. 

Just some quick notes explaining these two commands: 
"chown" changes the ownership of a file a file or directory. The -R option makes it recursive, meaning that it will also alter subdirectories of the target directory. This command can be used either to alter the owning user (i.e., chown  -R username  /home/username) or both the user and the group owning it (i.e., chown -R username:groupname /home/username). To view ownership, you can type 
```
ls -l
```
In the output, the third and fourth columns will show the user and group owners respectively.

"chmod" alters the permissions of a file or directory based on several criteria. In the system it users, there are three types of users: users, groups, and others. Again, the -R option changes things recursively. The numbers I've been using represent different combinations of access permissions for these three types of users. The most commonly used numbers are:
0 = no access
4 = read-only access
5 = read and execute files; no write access
6 = read and write to files; no executables
7 = read, write and execute

So, the command "chmod -R 774 /home/username" would make that directory and every subdirectory available like this:
primary user: full access
group users: full access
others: read-only access

To check on current permissions, you can type "ls -l" again. The first column will say something like this for each file:
```
-rwxr-xr-x
```
This is an alphabetic representation of the "755" permissions state. The user can do everything (rwx), the group can read and execute (r-x), and others can read and execute (r-x). The first dash might have a "d," which just means that it's a directory. 

So, that's the nutshell explanation. If you're looking for a good book, I highly recommend Scott Granneman's _Linux Phrasebook_, which is a really good introduction and reference book to the bash shell. It's gotten me out of many a jam in the past. :)

---

### Post by beanco on 2007-11-07
been very busy with other issues and work so I could not deal with this...

so i am about to do it.

```
Now, you'll want to make some modifications to those commands, since bodhi.zazen is addressing a single user situation. In the "chown" commands, change user_name to user_name:family. That will set both the user and group that owns the directory. With the "chmod" commands, change the second numeral to 7 so that group users (i.e., you) have full permissions. The last one can be 4 or 5.

```

so is it rob:family or aron:famliy? ie. me or aron? I know this is simple logic but it still baffles me....

Maybe I should go back and read the whole thread again... maybe it was all explained clearly there and I have just forgotten it.

At any rate,thanks for all the help!

robi

---

### Post by p_quarles on 2007-11-07
You want each user to be the owner of his/her .dmrc file, so for Aron's home folder (the one that's having the problems) it should be:
```
sudo chown aron:family .dmrc
```
In the thread I quoted from, though, that did not work (although oftentimes it will). If it doesn't, just go ahead and delete the file. A new one will automatically be created when the user logs in next. That's how the poster in that thread was able to resolve the issue.

If, for some reason, neither of those works, you'll probably just have to delete the account and create it anew. This is pretty straightforward, so it that's necessary, let me know and I'll provide instructions.

---

### Post by GameManK on 2007-11-07
The problem with this solution is that it only applies to the files that are already there.  If aron creates new files, they'll be owned by aron:aron and you won't be able to read them.

One way to solve this is to change aron's login group to family so that files created by him will be owned by aron:family

I think
```
sudo usermod -g family
```
is how you would do that.

I think the better solution would have been to instead add yourself to group aron.

---

### Post by p_quarles on 2007-11-07
> **GameManK said:**
> I think the better solution would have been to instead add yourself to group aron.
<slaps forehead> Yes, that is a much better solution.](*,) It completely escaped that me that every user is also a group. Thanks.

This way, you won't need to mess around with file permissions at all. After you've edited the /etc/sudoers and /etc/groups to give the children limited privileges, you can add yourself to their groups like so:
```
sudo addgroup rob aron
```

---

### Post by beanco on 2007-11-08
ok so i logn in as aron and make those changes.. .the one with the -g in it

does this mean i will not have to mess with his account, i mean delete it?


so, noce i have each persons account set up where they have the permissions I want them to... I can add myself to  their groups, giving myself the permission I want to have there... right?

Once that is done I can then be longged on as Robi and get to their stuff in terminal or even in gui if I want to, right?


robi

---

### Post by p_quarles on 2007-11-08
No, you don't need to use the "usermod -g" command. GameManK was making two different points there. The first was that the command I gave you ("chown aron:family /home/aron/*") would allow you to access *current* files without logging in as root, but it wouldn't give you access to any files created in the future under aron's account.

The second point was that it's much easier to just add yourself to aron's group. What I was overlooking was the fact that every user account automatically creates its own group. So, if you add your user to aron's group, you will be able to monitor all of his files from your account.

Basically, all you need to do is fix the .dmrc issue and then add your user to each of the kids' accounts, using the command I gave in my last post.

In other words, I was making things too complicated.:redface:

---

### Post by beanco on 2007-11-08
well, i made some mistake yesterday and ended up changing my own permissions.. now i ge tthe .dmrc msg too...

i will take care of me, of aron ... jus thav eto go back through the thread anf ind out how.. then do the groups stuff.

thanks for all the help

robi

---

### Post by beanco on 2007-11-09
I changed my permissions. that was easy.

I logged in as aron and tried the same thing but got the aron is not ni the sudoers list or sg to that effect.

so what is the next step to setting his permissions to he is the owner etc... once they are straightened out I can do the whole groups thing

thanks

robi

---

### Post by p_quarles on 2007-11-09
I don't quite understand . . . what were you doing when you got this error message?

---

### Post by beanco on 2007-11-10
Hi,

So, I logged on to Aron's account, opened up a terminal, and tried to change his permissions.


That is when I got the msg.. i.e. when i put in the first sudo command... as soon as I hit enter I got the msg.

Robi

---

### Post by p_quarles on 2007-11-10
Right, okay, you've already taken away Aron's permissions to run anything except updates and installations using "sudo." I'm not sure which command you're referring to, so could you spell it out, or point me to the post from which you took it?

The only thing I can recall is that a couple pages back I gave instructions for changing ownership and permissions from aron's account . . . but that doesn't need "sudo," because he's already the owner of those files.

---

### Post by beanco on 2007-11-11
so on page 4 was this:


```
sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown -R user_name /home/user_name
```

I did it to my own account when I messed up the permissions and was getting that .dmrc error msg, teh same one that Aron is getting.

So I tried this with Aron's account to no avail.

robi

---

### Post by beanco on 2007-11-11
> **beanco said:**
> so on page 4 was this:


```
sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown -R user_name /home/user_name
```

robi


I did it again, this time without sudo and it seems to work. I logged off and back on to Aron's account and did not get the .dmrc msg.

What you say about him being the owner, hence no need for sudo makes sense.

What does not makes sense is that when I did it for my own account I used sudo.

Oh, well...

I will now try to do what I had origniially asked. thanks for all the help

robi

---

### Post by p_quarles on 2007-11-11
> **beanco said:**
> What does not makes sense is that when I did it for my own account I used sudo.
Makes sense to me. Your account has full sudo privileges, so it can run any command as the root user. You didn't *need *to use sudo to change permissions on files that you own, but it won't stop you if you try.

---

### Post by beanco on 2007-11-11
well, when you put it that way it makes sense!

|I love how all this computer stuff makes so much sense.. too bad my brains does not function such that it grasps the logic of this stuff... but I am trying.
 
still have not set up the group family like you suggested earlier in this thread but tonight I hope to get to it!

robi

---

### Post by p_quarles on 2007-11-11
Like I said in [this]("http://ubuntuforums.org/showpost.php?p=3730882&postcount=40") post (and thanks to GamemanK's suggestions), I don't think you want to set up the family group. Just add your account to the "group" of each user you want to administrate. Like so:
```
sudo addgroup rob aron
```
I didn't make this very clear, but this advice supersedes the previous advice. The reason is outlined in GamemanK's post.

---

### Post by beanco on 2007-11-11
yeah, that's what I actually meant!!! sorry for being unclear!


```
sudo addgroup rob aron
```

Out of curiosity and again, this is because of my lack of a logical mind what this command means is that user ROB is being added to group ARON, right? 

Because group aron was created when i created user aron.

I assume, using this logic that

```
sudo addgroup rob ancsi
```

Would but user ROB in GROUP ancsi as when user account ancsi was created it generated a grou of the same name.


And that group family that was created can be removed using

```
sudo removegroup family
``` 

Or is this not a good idea, or the proper way of removing a group?

By removing a group the actually users are not affected, right?

robi

---

### Post by beanco on 2007-11-11
look what i got

```
rob@rob-desktop:~$ sudo addgroup rob aron
Password:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
The user `rob' is already a member of `aron'.
rob@rob-desktop:~$ 

```

nor sure what all the perl warnings are, though I have had that before, and I cannot remember how I rectified it.

but why is rob already a member of aron? Guess i did it earlier and forgot.

time to go back through this thread and see what the command is for checking group memberships.

robi

---

### Post by p_quarles on 2007-11-11
Yes, you're correct about the order of input for addgroup. 
```
sudo addgroup *username* *groupname*
```
And close enough on the command for getting rid of a group. It's actually "groupdel," but I wouldn't do that until you've got everything working smoothly.

To find the groups your user is in:
```
groups rob
```

---

### Post by beanco on 2007-11-11
thanks. 

i won't be deleting anything until everything is working !

so now I should be able to access everything in aron's account for instance.


I watned to check out some of his photos so in MC i went to /home/aron/photos and hit F3 on a photo i wanted to open. but i get
```

Cannot open WERWER.jpg
permission denied (13)
```

OK, maybe this is just an issue when using MC... but I wonder what the problem is?

I also tried places/file system/home/aron/photos and can see most of them. However I cannot see 3 that he added today. they hve a lock across them *their icons in file browser*

so what is the deal?

Again, thanks for the help

robi

edited to add

i checked properties/permissions and it says because I am not the owner I cannot change permissions.. that is fine, but I still want to see what the pics are... whats worse of all is that Aron wants me to look at these!!

---

### Post by p_quarles on 2007-11-11
My guess is that since I've given you several different strategies here, maybe they've accidentally overlapped a little. What's the output of this:
```
ls -l /home/aron/photos
```
Note that you don't need to post the entire output, just two or three file listings.

---

### Post by beanco on 2007-11-11
ok, here is what I got

only the first few lines..

```
rob@rob-desktop:~$ ls -l /home/aron/photos
total 354740
-rwx------ 1 aron aron     13394 Oct 28 18:12 DSC00053 (copy).JPG
-rwx------ 1 aron aron     16034 Oct 29 20:01 DSC00053.JPG
-rwx------ 1 aron aron     15632 Oct 29 19:53 DSC00054.JPG
-rwxrwxr-- 1 aron family 2257399 Oct  9 01:19 P1000042.JPG
-rwxrwxr-- 1 aron aron   1355578 Oct  9 01:21 P1000046.JPG
-rwxrwxr-- 1 aron aron   1988767 Oct  9 01:23 P1000049.JPG
-rwxrwxr-- 1 aron aron   2106562 Oct  9 01:24 P1000050.JPG
-rwxrwxr-- 1 aron aron   1821054 Oct  9 02:53 P1000052.JPG

```

after that they all look like this
```

-rwxrwxr-- 1 aron family 2003248 Oct  9 04:56 
```

robi

---

### Post by p_quarles on 2007-11-11
Okay, I think I see the problem, but don't have an immediate solution. I'm very curious about this myself, so I'll try to find some time to look into it tomorrow. 

Now, the problem (I think) is that the new files created by user aron on 10/28 and 10/29 are only accessible by owner. You indicated that he asked you to look at these photos recently, so I'm assuming it's those three that you had trouble accessing. 

What I don't quite get is why these newly created files were set up with those permissions. When I create new files, it automatically gives at least read privileges to group members. I'm going to look into how to change this setting.

In the meantime, there's an easy workaround. Login as aron, open a terminal, and run this command:
```
chmod -R 774 ~/photos/*
```
The same command will work on any other directory you need access to -- just substitute "photos" with the appropriate directory name. .

---

### Post by timnicholson on 2007-11-11
I've been hesitating to jump in here because I think the biggest problem is that the original poster is getting confused by all the advice. However, for folks that aren't totally up to speed on Unix permissions, using the command line can be a nightmare. Especially when trying to use the numeric representations of the security settings.

I just set this exact same scenario up for and old tablet pc I installed xubuntu on for the kids to use. I originally went too wide on the security and got the same errors upon login about how a users home directory shouldn't be writable by others, etc. So I ended up getting it set just right to accomplish what we are trying to accomplish here.

Its probably easiest to use the graphical security manager in ubuntu. Sign on as yourself (rob) and simply go to the kid's (aron's) home folder (/home/aron). Right click and choose properties. Click on the Permissions tab. You'll see the owner is the kid (aron). His access will say Read & Write. The group will say the kid (aron). Set the access to Read only. That will let you view his files but not add or delete. If you wanted to be able to write (add and change) then that's where you'd have to go back in to specific startup files and set them to read only as touched on in the above posts. If not, this is all you need to do. You can always sudo thunar or whatever file manager and get to whatever you want of theirs as well.

With setting the directory so that your group has read priveleges. New files created by the kid (aron) within his home directory should be viewable by you.

You've already done this I believe, but the other step would be to go into the Applications | System | Users and Groups option. Click on the Manage Groups button. Go down to the kid's group (aron) and double-click on it. You'll see a list of all users. Put a check next to your name (rob) to add you to his group. That way you can read (view) his stuff. He won't be able to read (view) yours because he's not a member of your group. I assume you don't want him to have access to your files.

I actually went one step further since I have 3 kids and myself that want to share SOME files with each other. We'll keep other "private" files in our own home directories. So I made a shared directory /home/shared. I used the graphical permissions screen to set that to Read & Write for owner, group, and others. This folder can be left wide open like that since its not anyone's home directory. 

Another nice thing about using the graphical method is I noticed a tab called Emblems next to the Permissions tab. It shows various folder icons that can be used and I chose one that is called "shared" which is an open hand that looks like the Windows icon for shared folders.

Another nice thing you can do is while having that shared folder highlighted, right click on it, choose Sent to and then Side Pane (Create Shortcut). This puts a nice shortcut in the file manager directly to the shared folder. Since you are still logged on as yourself at this point, you'll want to log on as the kid and do it for him as well (or have him do it) so its easy to find.

I hope this helps rather than adds to the confusion. I fibbed a bit about totally using the graphical method as I used to use unix in college and remembered some of this stuff, but I wouldn't have found the cool icon if I didn't also mess around in the graphical manager to double check what I did looked right.

---

### Post by beanco on 2007-11-12
p_quareles.

thanks for the help, again!!!! I will take care of things soon as I can.

Tim,

You are right in that I get confused with all the advice. You are also right that a graphical option is easier to udnertand than the command line way. 

But the command line is so cool! I would really like to learn it ... And permissions is one thing that I really need to come to graps well.

Maybe messing roudn with it a bit in the graphical way would make sense, then, once I actually understand all this permissions stuff and do not need to keep looking for help, I can return to the command line and learn that too.


Robi

---

