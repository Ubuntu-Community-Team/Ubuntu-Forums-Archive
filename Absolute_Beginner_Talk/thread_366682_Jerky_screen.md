---
title: "Jerky screen"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-02-21
Thanks to tseliot, I was able to install my NVIDIA driver yesterday so I now have my smooth scrolling and proper resolution.  I have now encountered another problem.  One that I can live with, but none the less annoying.

My screen will periodically jump or jerk.  I sometimes see brief flashes from another utility that might be open at the same time.  It doesn't happen all the time but when it does, it's quite annoying.

I don't have the problem in Windoze.

---

### Post by riven0 on 2007-02-21
Are you sure it's not a service running in the background that's causes these hiccups? Do you have beagle installed? Try posting the output of: **ps aux **

---

### Post by djen9999 on 2007-02-21
No, the first thing I checked for was something running in the background.  As a matter of fact, I was going to install beagle but I decided to wait until I got this cleared up.

---

### Post by djen9999 on 2007-02-21
Here's what I got from ps aux

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1632   532 ?        Ss   12:00   0:00 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    12:00   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   12:00   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    12:00   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   12:00   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   12:00   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   12:00   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   12:00   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   12:00   0:00 [kacpid]
root        11  0.0  0.0      0     0 ?        S<   12:00   0:00 [kacpi_notify]
root       164  0.0  0.0      0     0 ?        S<   12:00   0:00 [kseriod]
root       197  0.0  0.0      0     0 ?        S    12:00   0:00 [pdflush]
root       198  0.0  0.0      0     0 ?        S    12:00   0:00 [pdflush]
root       199  0.0  0.0      0     0 ?        S    12:00   0:00 [kswapd0]
root       200  0.0  0.0      0     0 ?        S<   12:00   0:00 [aio/0]
root      1675  0.0  0.0      0     0 ?        S<   12:00   0:00 [ata/0]
root      1679  0.0  0.0      0     0 ?        S<   12:00   0:00 [scsi_eh_0]
root      1680  0.0  0.0      0     0 ?        S<   12:00   0:00 [scsi_eh_1]
root      1801  0.0  0.0      0     0 ?        S<   12:00   0:00 [khubd]
root      1866  0.0  0.0      0     0 ?        S<   12:00   0:00 [kjournald]
root      1942  0.0  0.0   1600   544 ?        Ss   12:00   0:00 //sbin/logd
root      2088  0.0  0.1   2616  1044 ?        S<s  12:00   0:00 /sbin/udevd --d
root      2878  0.0  0.0      0     0 ?        S<   12:00   0:00 [shpchpd]
root      2885  0.0  0.0      0     0 ?        S<   12:00   0:00 [kpsmoused]
root      2912  0.0  0.0      0     0 ?        S<   12:00   0:00 [irda_sir_wq]
root      3056  0.0  0.0      0     0 ?        S<   12:00   0:00 [scsi_eh_2]
root      3057  0.0  0.0      0     0 ?        S<   12:00   0:00 [usb-storage]
dhcp      3419  0.0  0.0   2392   568 ?        S<s  12:00   0:00 dhclient3 -pf /
root      3729  0.0  0.0   1596   504 tty1     Ss+  12:00   0:00 /sbin/getty 384
root      3730  0.0  0.0   1596   500 tty2     Ss+  12:00   0:00 /sbin/getty 384
root      3731  0.0  0.0   1596   504 tty3     Ss+  12:00   0:00 /sbin/getty 384
root      3732  0.0  0.0   1600   508 tty4     Ss+  12:00   0:00 /sbin/getty 384
root      3733  0.0  0.0   1600   508 tty5     Ss+  12:00   0:00 /sbin/getty 384
root      3734  0.0  0.0   1600   508 tty6     Ss+  12:00   0:00 /sbin/getty 384
root      3943  0.0  0.1   2200  1152 ?        Ss   12:00   0:00 /usr/sbin/acpid
root      4032  0.0  0.0   1648   612 ?        Ss   12:00   0:00 /sbin/syslogd
root      4058  0.0  0.0   1724   508 ?        Ss   12:00   0:00 /bin/dd bs 1 if
klog      4060  0.0  0.1   2424  1304 ?        Ss   12:00   0:00 /sbin/klogd -P
root      4132  0.0  0.1  11800  1792 ?        Ss   12:00   0:00 /usr/sbin/gdm
root      4133  0.0  0.2  12164  2588 ?        S    12:00   0:00 /usr/sbin/gdm
root      4157  1.2  5.0  53192 48572 tty7     SLs+ 12:00   1:39 /usr/X11R6/bin/
cupsys    4170  0.0  0.2   4540  1984 ?        Ss   12:00   0:00 /usr/sbin/cupsd
root      4187  0.0  0.0   4900   928 ?        Ss   12:00   0:00 /usr/sbin/hpiod
hplip     4195  0.0  0.5   9672  4856 ?        S    12:00   0:00 python /usr/sbi
103       4243  0.0  0.0   2308   896 ?        Ss   12:00   0:00 /usr/bin/dbus-d
106       4258  0.0  0.5   7208  5672 ?        Ss   12:00   0:02 /usr/sbin/hald
root      4259  0.0  0.1   2916  1056 ?        S    12:00   0:00 hald-runner
106       4265  0.0  0.0   2028   808 ?        S    12:00   0:00 /usr/lib/hal/ha
djen9999  4273  0.0  1.1  20964 10676 ?        Ss   12:00   0:00 x-session-manag
106       4281  0.0  0.0   2024   812 ?        S    12:00   0:00 /usr/lib/hal/ha
106       4319  0.0  0.0   2032   840 ?        S    12:00   0:00 /usr/lib/hal/ha
djen9999  4323  0.0  0.0   4484   728 ?        Ss   12:01   0:00 /usr/bin/ssh-ag
djen9999  4326  0.0  0.0   2532   628 ?        S    12:01   0:00 /usr/bin/dbus-l
djen9999  4328  0.0  0.1   2308   988 ?        Ss   12:01   0:00 /usr/bin/dbus-d
106       4329  0.0  0.0   2032   840 ?        S    12:01   0:00 /usr/lib/hal/ha
106       4331  0.0  0.0   2028   836 ?        S    12:01   0:00 /usr/lib/hal/ha
106       4333  0.0  0.0   2032   840 ?        S    12:01   0:00 /usr/lib/hal/ha
djen9999  4336  0.0  0.3   6060  3564 ?        S    12:01   0:00 /usr/lib/libgco
106       4339  0.0  0.0   2032   840 ?        S    12:01   0:03 /usr/lib/hal/ha
djen9999  4360  0.0  0.0   2588   768 ?        S    12:01   0:00 /usr/bin/gnome-
djen9999  4363  0.0  0.9  28476  9556 ?        Sl   12:01   0:01 /usr/lib/contro
root      4368  0.0  1.1  13620 10864 ?        S    12:01   0:00 perl /usr/share
root      4396  0.0  0.0      0     0 ?        S<   12:01   0:00 [ondemand]
root      4415  0.0  0.1   5880  1344 ?        Ss   12:01   0:00 /usr/sbin/nmbd
djen9999  4418  0.0  0.0   1660   476 ?        Ss   12:01   0:00 /bin/sh -c /usr
djen9999  4419  0.0  0.3   4508  2992 ?        S    12:01   0:00 /usr/bin/esd -t
root      4420  0.0  0.2   8764  2136 ?        Ss   12:01   0:00 /usr/sbin/smbd
root      4463  0.0  0.0   8764   944 ?        S    12:01   0:00 /usr/sbin/smbd
root      4464  0.0  0.0   2072   716 ?        Ss   12:01   0:00 /usr/sbin/hcid
root      4473  0.0  0.0   1668   500 ?        Ss   12:01   0:00 /usr/sbin/sdpd
root      4484  0.0  0.0      0     0 ?        S<   12:01   0:00 [krfcommd]
daemon    4516  0.0  0.0   1852   424 ?        Ss   12:01   0:00 /usr/sbin/atd
root      4532  0.0  0.0   2192   860 ?        Ss   12:01   0:00 /usr/sbin/cron
djen9999  4610  0.2  0.9  16012  9416 ?        Ss   12:01   0:19 /usr/bin/metaci
djen9999  4626  0.1  1.9  60092 19108 ?        Ss   12:01   0:10 gnome-panel --s
djen9999  4628  0.1  3.2 102336 31132 ?        Ss   12:01   0:13 nautilus --no-d
djen9999  4632  0.0  0.3  39520  3084 ?        Ssl  12:01   0:00 /usr/lib/bonobo
djen9999  4636  0.0  0.3   8236  3328 ?        S    12:01   0:00 /usr/lib/gnome-
djen9999  4637  0.0  0.5  18252  5436 ?        Ss   12:01   0:00 gnome-volume-ma
djen9999  4647  0.0  1.1  50252 11192 ?        Ss   12:01   0:00 update-notifier
djen9999  4649  0.0  1.0  67204  9936 ?        Ssl  12:01   0:00 /usr/lib/evolut
djen9999  4658  0.0  0.8  47444  8348 ?        Ss   12:01   0:06 gnome-cups-icon
djen9999  4668  0.0  1.1  83256 10812 ?        S    12:01   0:00 /usr/lib/gnome-
djen9999  4669  0.0  0.7  48992  7264 ?        Ss   12:01   0:00 gnome-power-man
djen9999  4688  0.0  0.6  56972  6236 ?        Sl   12:01   0:00 /usr/lib/evolut
djen9999  4690  0.0  0.0   2508   944 ?        S    12:01   0:00 /usr/lib/nautil
djen9999  4695  0.0  0.9  27484  9136 ?        Sl   12:01   0:00 /usr/lib/evolut
djen9999  4716  0.0  1.2  51812 11656 ?        S    12:01   0:00 /usr/lib/gnome-
djen9999  4734  0.0  0.5  15924  5444 ?        Ss   12:01   0:02 gnome-screensav
djen9999  5052  0.0  0.0   1656   492 ?        S    12:11   0:00 /bin/sh /usr/bi
djen9999  5056  0.0  0.0   1660   504 ?        S    12:11   0:00 /bin/sh /usr/li
djen9999  5060  0.5  4.9 141588 47584 ?        Sl   12:11   0:37 /usr/lib/mozill
djen9999  5069  0.0  0.0      0     0 ?        Z    12:11   0:00 [net] <defunct>
djen9999  5085  1.8  5.7 220056 55832 ?        Sl   12:12   2:13 /usr/lib/firefo
djen9999  5110  0.0  0.0      0     0 ?        Z    12:12   0:00 [net] <defunct>
root      7300  0.0  0.0      0     0 ?        S<   13:21   0:00 [xfslogd/0]
root      7301  0.0  0.0      0     0 ?        S<   13:21   0:00 [xfsdatad/0]
root      7308  0.0  0.0      0     0 ?        S<   13:21   0:00 [jfsIO]
root      7309  0.0  0.0      0     0 ?        S<   13:21   0:00 [jfsCommit]
root      7310  0.0  0.0      0     0 ?        S<   13:21   0:00 [jfsSync]
djen9999  9228  6.8  1.5  70848 14856 ?        Sl   14:09   0:00 gnome-terminal
djen9999  9230  0.0  0.0   2504   800 ?        S    14:09   0:00 gnome-pty-helpe
djen9999  9231  2.4  0.3   5396  2996 pts/0    Ss   14:09   0:00 bash
djen9999  9252  0.0  0.1   2472   984 pts/0    R+   14:09   0:00 ps aux
djen9999@djen9999-desktop:~$

---

### Post by djen9999 on 2007-02-22
I think I hit upon the problem.

Since I wasn't having this problem in Windows, I decided to check my Windows settings.  Everything is the same except for the refresh rate.  It's set at 60 in Windows and 76 in Ubuntu.  I went to System>Preferences>Screen Resolution but it will only allow me to change the resolution, when I click on refresh rate, it doesn't give me any option other than 76.

What now?

---

### Post by djen9999 on 2007-02-22
Sorry, that should be 75 Hz not 76.

---

### Post by MkfIbK7a on 2007-02-22
do 

> sudo dpkg-reconfigure xserver-xorg

answer the questions correctly and the last question should ask simple medium or advanced choose medium or advanced an you will be able to set your refresh rate.

---

### Post by djen9999 on 2007-02-22
I answered all the questions, set the refresh rate to 60 Hz.and nothing changed.  It was if I hadn't done anything.  Even the settings in System>Preferences>Screen Resolution didn't change.Refresh is still at 75Hz.

Looking back, here is the error message I got:

~$ sudo dpkg-reconfigure xserver-xorg
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070222152514
dexconf: error: cannot generate configuration file; shared/default-x-server not 
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct 
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.

I have no idea where to go from here.

---

