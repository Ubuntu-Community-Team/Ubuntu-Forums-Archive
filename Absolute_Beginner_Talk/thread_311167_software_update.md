---
title: "software update"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-12-02
Hi,
I am using Dapler Drake and update notifier button is blinking right now at the top.

When I try to update my system, I receive the following error message: 
> Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

however, there no another software management tool installed in my machine.

see below for the result of the ps -aux

I would appreciate any help on my problem:

mozkaynak@ubuntu:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   1564   528 ?        S    11:39   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   11:39   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    11:39   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   11:39   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   11:39   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   11:39   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   11:39   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   11:39   0:00 [kacpid]
root       104  0.0  0.0      0     0 ?        S    11:39   0:00 [pdflush]
root       105  0.0  0.0      0     0 ?        S    11:39   0:00 [pdflush]
root       107  0.0  0.0      0     0 ?        S<   11:39   0:00 [aio/0]
root       106  0.0  0.0      0     0 ?        S    11:39   0:00 [kswapd0]
root       694  0.0  0.0      0     0 ?        S<   11:39   0:00 [kseriod]
root      1818  0.0  0.0      0     0 ?        S<   11:39   0:00 [ata/0]
root      1819  0.0  0.0      0     0 ?        S<   11:39   0:00 [ata_hotplug/0]
root      1822  0.0  0.0      0     0 ?        S<   11:39   0:00 [scsi_eh_0]
root      1823  0.0  0.0      0     0 ?        S<   11:39   0:00 [scsi_eh_1]
root      1843  0.0  0.0      0     0 ?        S<   11:39   0:00 [khubd]
root      1860  0.0  0.0      0     0 ?        S    11:39   0:00 [khpsbpkt]
root      1874  0.0  0.0      0     0 ?        S    11:39   0:00 [knodemgrd_0]
root      1991  0.0  0.0      0     0 ?        S    11:39   0:00 [kjournald]
root      2169  0.0  0.0   2436   924 ?        S<s  11:39   0:00 /sbin/udevd --d
root      2963  0.0  0.0      0     0 ?        S    11:39   0:00 [shpchpd_event]
root      3069  0.0  0.0      0     0 ?        S<   11:39   0:00 [kgameportd]
root      3539  0.0  0.0      0     0 ?        S    11:39   0:00 [kjournald]
dhcp      3548  0.0  0.0   2340   640 ?        S<s  11:39   0:00 dhclient3 -pf /
root      3561  0.0  0.0      0     0 ?        S    11:39   0:00 [kjournald]
root      3562  0.0  0.0      0     0 ?        S    11:39   0:00 [kjournald]
root      3944  0.0  0.1   2156  1200 ?        Ss   11:39   0:00 /usr/sbin/acpid
syslog    4037  0.0  0.0   1768   692 ?        Ss   11:39   0:00 /sbin/syslogd -
root      4063  0.0  0.0   1680   496 ?        Ss   11:39   0:00 /bin/dd bs 1 if
klog      4065  0.0  0.1   2412  1340 ?        Ss   11:39   0:00 /sbin/klogd -P
105       4084  0.0  0.0   2192   848 ?        Ss   11:39   0:00 /usr/bin/dbus-d
114       4099  0.1  0.5   6908  5504 ?        Ss   11:39   0:00 /usr/sbin/hald
root      4100  0.0  0.0   2716   976 ?        S    11:39   0:00 hald-runner
114       4105  0.0  0.0   2008   796 ?        S    11:39   0:00 /usr/lib/hal/ha
114       4159  0.0  0.0   2008   796 ?        S    11:39   0:00 /usr/lib/hal/ha
114       4166  0.0  0.0   2008   816 ?        S    11:39   0:00 /usr/lib/hal/ha
114       4167  0.0  0.0   2008   816 ?        S    11:39   0:00 /usr/lib/hal/ha
114       4169  0.0  0.0   2012   864 ?        S    11:39   0:00 /usr/lib/hal/ha
114       4170  0.0  0.0   2008   860 ?        S    11:39   0:00 /usr/lib/hal/ha
root      4430  0.0  0.1  10912  1792 ?        Ss   11:39   0:00 /usr/sbin/gdm
root      4438  0.0  0.2  11264  2520 ?        S    11:39   0:00 /usr/sbin/gdm
root      4456  2.5  2.9  36080 30292 tty7     RLs+ 11:39   0:15 /usr/bin/X :0 -
cupsys    4480  0.0  0.1   4396  1996 ?        Ss   11:39   0:00 /usr/sbin/cupsd
hplip     4501  0.0  0.0  12872   916 ?        Ssl  11:40   0:00 /usr/sbin/hpiod
hplip     4504  0.0  0.4   9408  4676 ?        S    11:40   0:00 python /usr/sbi
clamav    4607  0.0  0.1   5220  1164 ?        Ss   11:40   0:00 /usr/bin/freshc
root      4667  0.0  0.0   4764  1028 ?        Ss   11:40   0:00 /usr/sbin/sshd
root      4713  0.0  0.0   1968   712 ?        Ss   11:40   0:00 hcid: processin
root      4721  0.0  0.0   1616   456 ?        Ss   11:40   0:00 /usr/sbin/sdpd
root      4733  0.0  0.0      0     0 ?        S<   11:40   0:00 [krfcommd]
root      4747  0.0  0.0   1624   292 ?        Ss   11:40   0:00 /sbin/mdadm -F
daemon    4781  0.0  0.0   1804   400 ?        Ss   11:40   0:00 /usr/sbin/atd
root      4794  0.0  0.0   2120   840 ?        Ss   11:40   0:00 /usr/sbin/cron
root      4839  0.0  0.2   7776  2364 ?        Ss   11:40   0:00 /usr/sbin/apach
www-data  4846  0.0  0.1   7568  1676 ?        S    11:40   0:00 /usr/sbin/apach
www-data  4847  0.0  0.2 229108  2104 ?        Sl   11:40   0:00 /usr/sbin/apach
www-data  4849  0.0  0.2 229108  2108 ?        Sl   11:40   0:00 /usr/sbin/apach
root      4973  0.0  0.0   1564   492 tty1     Ss+  11:40   0:00 /sbin/getty 384
root      4974  0.0  0.0   1564   496 tty2     Ss+  11:40   0:00 /sbin/getty 384
1000      4981  0.0  1.0  19820 10360 ?        Ss   11:40   0:00 x-session-manag
1000      5027  0.0  0.0   4332   688 ?        Ss   11:40   0:00 /usr/bin/ssh-ag
1000      5030  0.0  0.0   2716   656 ?        S    11:40   0:00 /usr/bin/dbus-l
1000      5031  0.0  0.0   2196   944 ?        Ss   11:40   0:00 dbus-daemon --f
1000      5033  0.0  0.3   6316  3880 ?        S    11:40   0:00 /usr/lib/libgco
1000      5036  0.0  0.0   2344   732 ?        S    11:40   0:00 /usr/bin/gnome-
1000      5038  0.0  0.2   6280  2928 ?        Ss   11:40   0:00 /usr/lib/bonobo
1000      5040  0.0  0.8  27428  9236 ?        Sl   11:40   0:00 /usr/lib/contro
1000      5042  0.0  0.4   5812  4256 ?        Ss   11:40   0:00 /usr/bin/esd -t
1000      5050  0.3  0.8  15280  9268 ?        Ss   11:40   0:02 /usr/bin/metaci
1000      5055  0.2  1.4  70152 15436 ?        Ssl  11:40   0:01 gnome-panel --s
1000      5057  0.1  1.5 109180 15716 ?        Ssl  11:40   0:00 nautilus --no-d
1000      5060  0.0  0.5  17124  5312 ?        Ss   11:40   0:00 gnome-volume-ma
1000      5077  0.0  0.9  71220  9824 ?        S    11:40   0:00 /usr/lib/notifi
1000      5080  0.0  0.3   8500  3780 ?        Sl   11:40   0:00 /usr/lib/gnome-
1000      5082  0.0  1.1  67088 11424 ?        Ss   11:40   0:00 update-notifier
1000      5094  0.1  2.2  44820 23256 ?        Sl   11:40   0:00 beagled --debug
1000      5097  0.0  0.8  38236  8532 ?        Ss   11:40   0:00 gnome-cups-icon
1000      5104  0.0  0.8  98188  8544 ?        Sl   11:40   0:00 /usr/lib/gnome-
1000      5105  0.0  0.5  17724  5508 ?        Ss   11:40   0:00 gnome-power-man
1000      5116  0.0  0.0   2284   800 ?        S    11:40   0:00 /usr/lib/nautil
1000      5131  0.0  0.9  23104 10320 ?        S    11:40   0:00 /usr/lib/gnome-
1000      5133  0.0  1.1  67844 11504 ?        S    11:40   0:00 /usr/lib/gnome-
1000      5153  0.0  0.2  14620  2800 ?        Ss   11:40   0:00 gnome-screensav
1000      5250  0.4  1.5  26600 15708 ?        S    11:42   0:02 lyx-qt
1000      5649  3.7  4.2 157680 44524 ?        Sl   11:42   0:16 /usr/lib/firefo
1000      5708  0.0  0.4  11532  4948 ?        S    11:44   0:00 /usr/bin/gksu -
root      5709  0.1  1.8  83036 19308 ?        Ssl  11:44   0:00 /usr/bin/python
root      5711  0.0  0.3   6192  3708 ?        S    11:44   0:00 /usr/lib/libgco
1000      5849  7.5  1.3  39620 14432 ?        Sl   11:50   0:00 gnome-terminal
1000      5850  0.0  0.0   2288   688 ?        S    11:50   0:00 gnome-pty-helpe
1000      5851  0.0  0.1   4472  2044 pts/0    Ss   11:50   0:00 bash
1000      5853  0.0  0.0   2400  1020 pts/0    R+   11:50   0:00 ps -aux

---

### Post by pissedoffdude on 2006-12-02
Try rebooting your computer.  I had that problem once and rebooting it took care if it.

---

### Post by mozkaynak on 2006-12-02
I have already done that. this did not work.
thanks for your help though.
any other suggestion?

---

### Post by HokeyFry on 2006-12-02
open the System Monitor and look for a program that might be conflicting with what your trying to open. then close the thread (can be dangerous in some cases, be careful).

---

