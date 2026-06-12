---
title: "HELP!!! very strange question"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-03
i pressed alt+F2 got the "run" application i then typed regedit my computer came up with MICROSOFT REGEDIT!! i did 
```
ps aux
```
and one of the applications were regedit.exe
is this normal?

---

### Post by pay on 2007-01-03
wine uses regedit

---

### Post by Denn1s on 2007-01-03
it happens to me to, its wine's regedit for wath i can see

---

### Post by MkfIbK7a on 2007-01-03
thx for replying
```
jon@albert:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1632   472 ?        Ss   Jan01   0:02 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    Jan01   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   Jan01   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Jan01   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   Jan01   0:13 [events/0]
root         6  0.0  0.0      0     0 ?        S<   Jan01   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   Jan01   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   Jan01   0:00 [kblockd/0]
root        28  0.0  0.0      0     0 ?        S<   Jan01   0:00 [kseriod]
root        70  0.0  0.0      0     0 ?        S    Jan01   0:01 [pdflush]
root        71  0.0  0.0      0     0 ?        S    Jan01   0:00 [pdflush]
root        72  0.0  0.0      0     0 ?        S    Jan01   0:04 [kswapd0]
root        73  0.0  0.0      0     0 ?        S<   Jan01   0:00 [aio/0]
root      1649  0.0  0.0      0     0 ?        S<   Jan01   0:00 [khubd]
root      1704  0.0  0.0      0     0 ?        S<   Jan01   0:06 [kjournald]
root      1779  0.0  0.1   1604   444 ?        Ss   Jan01   0:00 //sbin/logd
root      1892  0.0  0.0   2604   320 ?        S<s  Jan01   0:01 /sbin/udevd --d
root      2632  0.0  0.0      0     0 ?        S<   Jan01   0:00 [shpchpd]
root      2672  0.0  0.0      0     0 ?        S<   Jan01   0:00 [kgameportd]
root      2732  0.0  0.0      0     0 ?        S<   Jan01   0:00 [kpsmoused]
root      2899  0.0  0.0      0     0 ?        S<   Jan01   0:20 [wrap_wq]
root      2900  0.0  0.0      0     0 ?        S<   Jan01   0:00 [ndis_wq]
root      3308  0.0  0.1   1596   412 tty1     Ss+  Jan01   0:00 /sbin/getty 384
root      3309  0.0  0.1   1596   412 tty2     Ss+  Jan01   0:00 /sbin/getty 384
root      3310  0.0  0.1   1600   412 tty3     Ss+  Jan01   0:00 /sbin/getty 384
root      3311  0.0  0.1   1596   412 tty4     Ss+  Jan01   0:00 /sbin/getty 384
root      3312  0.0  0.1   1596   412 tty5     Ss+  Jan01   0:00 /sbin/getty 384
root      3313  0.0  0.1   1600   412 tty6     Ss+  Jan01   0:00 /sbin/getty 384
root      3462  0.0  0.1   1720   380 ?        Ss   Jan01   0:00 /bin/dd bs 1 if
klog      3464  0.0  0.1   2424   368 ?        Ss   Jan01   0:00 /sbin/klogd -P
root      3536  0.0  0.3  11796  1092 ?        Ss   Jan01   0:00 /usr/sbin/gdm -
root      3593  0.0  0.1   4904   552 ?        Ss   Jan01   0:00 /usr/sbin/hpiod
hplip     3602  0.0  0.3   9672  1004 ?        S    Jan01   0:02 python /usr/sbi
root      3634  0.0  0.0      0     0 ?        S    Jan01   0:00 [kapmd]
root      3645  0.0  0.1   1600   368 ?        Ss   Jan01   0:00 /usr/sbin/apmd
103       3667  0.0  0.2   2296   840 ?        Ss   Jan01   0:01 /usr/bin/dbus-d
106       3696  0.0  0.5   7004  1784 ?        Ss   Jan01   0:20 /usr/sbin/hald
root      3697  0.0  0.2   2912   832 ?        S    Jan01   0:00 hald-runner
106       3914  0.0  0.1   2024   636 ?        S    Jan01   0:01 /usr/lib/hal/ha
106       3931  0.0  0.2   2024   696 ?        S    Jan01   0:10 /usr/lib/hal/ha
root      3991  0.0  0.1  13748   496 ?        S    Jan01   0:00 perl /usr/share
daemon    4083  0.0  0.0   1852   312 ?        Ss   Jan01   0:00 /usr/sbin/atd
root      4096  0.0  0.2   2196   660 ?        Ss   Jan01   0:00 /usr/sbin/cron
dhcp      4267  0.0  0.1   2396   452 ?        S<s  Jan01   0:00 dhclient3 -pf /
cupsys    4799  0.0  0.2   4536   744 ?        SNs  Jan01   0:00 /usr/sbin/cupsd
root      8880  0.0  0.5  12152  1640 ?        S    Jan01   0:00 /usr/sbin/gdm -
root      8883  6.9  6.3 222560 20424 tty7     Ss+  Jan01 124:58 /usr/bin/X :0 -
jon       8900  0.0  2.2  20808  7104 ?        Ss   Jan01   0:01 /usr/bin/gnome-
jon       8936  0.0  0.0   4484   268 ?        Ss   Jan01   0:00 /usr/bin/ssh-ag
jon       8939  0.0  0.1   2528   492 ?        S    Jan01   0:00 /usr/bin/dbus-l
jon       8940  0.0  0.2   2292   888 ?        Ss   Jan01   0:03 /usr/bin/dbus-d
jon       8942  0.0  0.8   5624  2796 ?        S    Jan01   0:05 /usr/lib/libgco
jon       8945  0.0  0.1   2584   572 ?        S    Jan01   0:00 /usr/bin/gnome-
jon       8948  0.0  2.0  28908  6716 ?        Sl   Jan01   0:20 /usr/lib/contro
jon       8971  0.2  2.4  16108  7820 ?        Ss   Jan01   4:57 /usr/bin/metaci
jon       8976  0.2  5.6 111540 18060 ?        Ss   Jan01   3:54 gnome-panel --s
jon       8978  0.1  5.6 118880 18168 ?        Ss   Jan01   1:49 nautilus --no-d
jon       8982  0.0  0.8  39480  2728 ?        Ssl  Jan01   0:02 /usr/lib/bonobo
jon       8987  0.0  2.7  52984  8832 ?        Ss   Jan01   0:14 update-notifier
jon       8992  0.0  0.8   8308  2724 ?        S    Jan01   0:00 /usr/lib/gnome-
jon       9009  0.0  2.5  83412  8140 ?        S    Jan01   0:02 /usr/lib/gnome-
jon       9025  0.0  0.2   2504   760 ?        S    Jan01   0:00 /usr/lib/nautil
jon       9040  0.0  1.9  50512  6240 ?        Ss   Jan01   0:05 gnome-power-man
jon       9043  0.0  2.5  52260  8092 ?        S    Jan01   0:06 /usr/lib/gnome-
jon       9060  0.0  0.5   5348  1616 ?        S    Jan01   0:09 xscreensaver -n
jon       9252  0.0  0.5  10604  1788 ?        S    Jan01   0:02 /usr/bin/artsd
jon       9729  0.0  2.4  48200  7832 ?        S    Jan01   0:13 /usr/lib/notifi
jon      10330  0.1  1.9  35408  6332 ?        S    Jan02   1:57 /usr/lib/at-spi
root     12191  0.0  0.1   1652   564 ?        SNs  Jan02   0:00 /sbin/syslogd
jon      14684  0.0  1.2  12264  4020 ?        S    Jan02   0:24 /usr/bin/gksu -
root     14685  0.0  0.2   2548   784 ?        Ss   Jan02   0:00 /usr/bin/sudo -
jon      15189  0.0  3.1  66464 10176 ?        S    Jan02   0:18 gaim
jon      15199  0.6  4.3  32876 14112 ?        Sl   Jan02   2:50 skype
jon      15360  4.0  5.0 135868 16068 ?        Sl   Jan02  18:12 rhythmbox
jon      17147 19.5 35.2 303512 113208 ?       Sl   Jan02  23:59 /usr/lib/firefo
jon      17159  0.0  0.0      0     0 ?        Z    Jan02   0:00 [net] <defunct>
jon      17538  0.0  0.1   1660   496 ?        S    00:30   0:00 /bin/sh /usr/bi
jon      17554  4.8  4.5  32276 14440 ?        Sl   00:30   1:59 /usr/bin/python
jon      17563  0.4  0.7   3928  2248 ?        S    00:30   0:09 /usr/bin/festiv
jon      17566  0.0  4.0  17788 12900 ?        S    00:30   0:00 festival --serv
jon      17567  8.4  8.9  33696 28608 ?        R    00:30   3:28 festival --serv
jon      17568  0.1  1.0   7432  3224 ?        S    00:30   0:04 /usr/lib/festiv
**jon      18684  6.7  2.6 2651004 8604 ?        S    01:10   0:02 regedit.exe   **
jon      18700 18.5  5.0  72012 16060 ?        Sl   01:10   0:06 gnome-terminal
jon      18709  1.5  0.5   4084  1656 ?        Ss   01:10   0:00 /usr/bin/../lib
jon      18714  0.0  0.2   2504   804 ?        S    01:11   0:00 gnome-pty-helpe
jon      18715  4.5  0.9   5520  3120 pts/0    Ss   01:11   0:00 bash
jon      18738 17.5  2.4 2650756 7876 ?        Ssl  01:11   0:02 c:\windows\syst
jon      18745  0.0  0.3   2472   984 pts/0    R+   01:11   0:00 ps -aux
jon@albert:~$ 

```
also a screen shot
can you tell me if you see anything strange in my ps output (other than regedit)?

---

### Post by jblebrun on 2007-01-03
There's nothing at all strange in your ps output. The regedit.exe is also not strange, since you did execute it, and it is running, via WINE. So everythign looks normal. :-)

---

### Post by MkfIbK7a on 2007-01-03
k thx again

---

### Post by borris.morris on 2007-02-10
yep, no different than the wine config via winecfg.

---

