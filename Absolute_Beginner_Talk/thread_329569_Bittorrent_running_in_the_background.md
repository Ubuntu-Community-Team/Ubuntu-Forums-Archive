---
title: "Bittorrent running in the background??"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-01-01
Last time I shut down, I saw a message reading something to the effect of: stopping torrent tracking

I have bitTorrent, bittornado, and azureus installed, but haven't used them in the past 3 weeks. Why would this process be running?

-Andrew

---

### Post by Pobega on 2007-01-01
Why don't you try 

*ps aux* 

in a terminal and post what you get here? Unless of course, there is a better command for this.

---

### Post by Atreus12 on 2007-01-01
> agrieser@andrew:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1568   532 ?        S    14:18   0:01 init [2]
root         2  0.0  0.0      0     0 ?        S    14:18   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   14:18   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    14:18   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   14:18   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   14:18   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   14:18   0:00 [kthread]
root         9  0.0  0.0      0     0 ?        S<   14:18   0:00 [kblockd/0]
root        10  0.0  0.0      0     0 ?        S<   14:18   0:00 [kacpid]
root       109  0.0  0.0      0     0 ?        S    14:18   0:00 [pdflush]
root       112  0.0  0.0      0     0 ?        S<   14:18   0:00 [aio/0]
root       111  0.0  0.0      0     0 ?        S    14:18   0:00 [kswapd0]
root       700  0.0  0.0      0     0 ?        S<   14:18   0:00 [kseriod]
root      1869  0.0  0.0      0     0 ?        S<   14:18   0:00 [ata/0]
root      1870  0.0  0.0      0     0 ?        S<   14:18   0:00 [ata_hotplug/0]
root      1874  0.0  0.0      0     0 ?        S<   14:18   0:00 [scsi_eh_0]
root      1875  0.0  0.0      0     0 ?        S<   14:18   0:00 [scsi_eh_1]
root      1896  0.0  0.0      0     0 ?        S<   14:18   0:00 [khubd]
root      1915  0.0  0.0      0     0 ?        S    14:18   0:00 [khpsbpkt]
root      1949  0.0  0.0      0     0 ?        S    14:18   0:00 [knodemgrd_0]
root      2051  0.0  0.0      0     0 ?        S    14:18   0:00 [kjournald]
root      2284  0.0  0.0   2428   920 ?        S<s  14:18   0:00 /sbin/udevd --d
root      3100  0.0  0.0      0     0 ?        S    14:18   0:00 [shpchpd_event]
root      3268  0.0  0.0      0     0 ?        S<   14:18   0:00 [kgameportd]
root      3687  0.0  0.0      0     0 ?        S    14:18   0:00 [kjournald]
root      3688  0.0  0.0      0     0 ?        S    14:18   0:01 [kjournald]
root      3800  0.0  0.0      0     0 ?        S<   14:19   0:00 [wrap_wq]
root      3801  0.0  0.0      0     0 ?        S<   14:19   0:06 [ndis_wq]
root      4162  0.0  0.1   2156  1196 ?        Ss   14:19   0:00 /usr/sbin/acpid
root      4292  0.0  0.0   1680   496 ?        Ss   14:19   0:00 /bin/dd bs 1 if
klog      4294  0.0  0.1   2388  1312 ?        Ss   14:19   0:00 /sbin/klogd -P
root      4609  0.0  0.1  10912  1804 ?        Ss   14:19   0:00 /usr/sbin/gdm
root      4638  0.0  0.2  11384  2620 ?        S    14:19   0:00 /usr/sbin/gdm
root      4647  2.9  3.6  47488 38060 tty7     SLs+ 14:19  12:41 /usr/bin/X :0 -
hplip     4648  0.0  0.0  12876   920 ?        Ssl  14:19   0:00 /usr/sbin/hpiod
hplip     4655  0.0  0.4   9412  4680 ?        S    14:19   0:00 python /usr/sbi
104       4745  0.0  0.0   2192   896 ?        Ss   14:19   0:00 /usr/bin/dbus-d
108       4760  0.0  0.5   6980  5576 ?        Ss   14:19   0:01 /usr/sbin/hald
root      4761  0.0  0.0   2716   976 ?        S    14:19   0:00 hald-runner
108       4766  0.0  0.0   2004   792 ?        S    14:19   0:00 /usr/lib/hal/ha
108       4816  0.0  0.0   2004   792 ?        S    14:19   0:00 /usr/lib/hal/ha
108       4833  0.0  0.0   2012   864 ?        S    14:19   0:03 /usr/lib/hal/ha
108       4834  0.0  0.0   2012   864 ?        S    14:19   0:03 /usr/lib/hal/ha
108       4836  0.0  0.0   2012   820 ?        S    14:19   0:02 /usr/lib/hal/ha
108       4837  0.0  0.0   2012   864 ?        S    14:19   0:02 /usr/lib/hal/ha
root      4864  0.0  0.0   1932   684 ?        Ss   14:19   0:00 /sbin/dhcdbd --
root      4881  0.0  0.1   3924  1864 ?        Ss   14:19   0:00 /usr/sbin/Netwo
root      4895  0.0  0.1   2808  1064 ?        Ss   14:19   0:00 /usr/sbin/Netwo
root      4919  0.0  0.1   2096  1056 ?        S    14:19   0:00 /usr/sbin/hddte
root      5061  0.0  0.1   5772  1416 ?        Ss   14:19   0:00 /usr/sbin/nmbd
root      5063  0.0  0.2   8432  2164 ?        Ss   14:19   0:00 /usr/sbin/smbd
root      5109  0.0  0.0   8432   912 ?        S    14:19   0:00 /usr/sbin/smbd
ntp       5125  0.0  0.3   3588  3588 ?        SLs  14:19   0:00 /usr/sbin/ntpd
root      5143  0.0  0.0   3588  1012 ?        S    14:19   0:00 /usr/sbin/ntpd
root      5144  0.0  0.0   1968   712 ?        Ss   14:19   0:00 hcid: processin
root      5151  0.0  0.0   1620   460 ?        Ss   14:19   0:00 /usr/sbin/sdpd
root      5162  0.0  0.0      0     0 ?        S<   14:19   0:00 [krfcommd]
root      5177  0.0  0.0   1628   296 ?        Ss   14:19   0:00 /sbin/mdadm -F
daemon    5217  0.0  0.0   1804   400 ?        Ss   14:19   0:00 /usr/sbin/atd
root      5236  0.0  0.0   2120   844 ?        Ss   14:19   0:00 /usr/sbin/cron
root      5352  0.0  0.0   1560   492 tty1     Ss+  14:19   0:00 /sbin/getty 384
root      5358  0.0  0.0   1560   488 tty2     Ss+  14:19   0:00 /sbin/getty 384
root      5361  0.0  0.0   1564   496 tty3     Ss+  14:19   0:00 /sbin/getty 384
root      5364  0.0  0.0   1564   496 tty4     Ss+  14:19   0:00 /sbin/getty 384
root      5367  0.0  0.0   1560   492 tty5     Ss+  14:19   0:00 /sbin/getty 384
root      5370  0.0  0.0   1560   492 tty6     Ss+  14:19   0:00 /sbin/getty 384
root      5434  0.0  0.0   3344   964 ?        S<s  14:19   0:00 /sbin/wpa_suppl
dhcp      5464  0.0  0.0   2336   544 ?        S<s  14:19   0:00 dhclient3 -pf /
agrieser  5609  0.0  0.3   6064  3684 ?        S    14:21   0:00 /usr/lib/libgco
agrieser  5625  0.0  1.0  20104 10644 ?        Ss   14:21   0:00 x-session-manag
agrieser  5667  0.0  0.0   4336   688 ?        Ss   14:21   0:00 /usr/bin/ssh-ag
agrieser  5670  0.0  0.0   2196   908 ?        Ss   14:21   0:00 dbus-daemon --f
agrieser  5671  0.0  0.0   2716   652 ?        S    14:21   0:00 /usr/bin/dbus-l
agrieser  5674  0.0  0.0   2344   808 ?        S    14:21   0:00 /usr/bin/gnome-
agrieser  5676  0.0  0.2   6268  2932 ?        Ss   14:21   0:00 /usr/lib/bonobo
agrieser  5678  0.0  0.4   5796  4272 ?        Ss   14:21   0:00 /usr/bin/esd -t
agrieser  5680  0.0  0.8  27436  9260 ?        Sl   14:21   0:05 /usr/lib/contro
agrieser  5691  0.4  0.9  16020 10164 ?        Ss   14:21   2:01 /usr/bin/metaci
agrieser  5697  0.2  2.9  50688 30208 ?        Ssl  14:21   0:53 gnome-panel --s
agrieser  5699  0.1  4.2  96836 43500 ?        Ssl  14:21   0:41 nautilus --no-d
agrieser  5706  0.0  0.1   4152  1584 ?        Ss   14:21   0:00 /bin/bash /home
agrieser  5708  0.0  1.0  19380 10636 ?        Ss   14:21   0:01 update-notifier
agrieser  5712  0.0  0.5  17128  5320 ?        Ss   14:21   0:00 gnome-volume-ma
agrieser  5716  0.0  0.6  46016  6224 ?        Sl   14:21   0:00 /usr/lib/gnome-
agrieser  5732  0.0  1.3  61324 13608 ?        Sl   14:21   0:01 /usr/lib/gnome-
agrieser  5740  0.0  0.7  37708  7896 ?        Ss   14:21   0:02 gnome-cups-icon
agrieser  5744  0.0  0.5  17732  5552 ?        Ss   14:21   0:00 gnome-power-man
agrieser  5746  0.0  0.0   2288   804 ?        S    14:21   0:00 /usr/lib/nautil
agrieser  5749  0.0  1.0  23396 10692 ?        S    14:21   0:00 /usr/lib/gnome-
agrieser  5751  0.0  1.1  34856 11928 ?        S    14:21   0:00 /usr/lib/gnome-
agrieser  5754  0.3  0.1   4252  1732 ?        S    14:21   1:32 conky
agrieser  5786  0.0  0.2  14624  2908 ?        Ss   14:22   0:06 gnome-screensav
agrieser  5901  0.0  0.1   4184  1692 ?        S    14:24   0:00 /bin/sh /usr/bi
agrieser  5905  0.0  0.1   4224  1720 ?        S    14:24   0:00 /bin/sh /usr/li
agrieser  5910  0.0  4.1  99644 42916 ?        Sl   14:24   0:08 /usr/lib/mozill
agrieser  5915  0.0  1.7  44804 18600 ?        S    14:24   0:10 gaim
cupsys    6017  0.0  0.1   4200  1892 ?        SNs  14:24   0:01 /usr/sbin/cupsd
root      6030  0.0  0.2   5632  2856 ?        Ss   14:24   0:00 nessusd: waitin
syslog    6188  0.0  0.0   1764   708 ?        SNs  14:25   0:00 /sbin/syslogd -
root      6300  0.0  0.0      0     0 ?        S    14:28   0:00 [pdflush]
agrieser  6671  0.6  4.7 125688 48628 ?        Sl   14:34   2:43 /usr/lib/firefo
agrieser  8165  0.1  1.0  49592 11180 ?        SLl  15:01   0:46 xmms
agrieser 20863  0.0  0.4  48984  4668 ?        Ss   21:20   0:00 xmms
agrieser 20879  3.1  5.0  90444 51716 ?        Sl   21:21   0:21 gimp --display
agrieser 20880  0.0  0.4  13192  4188 ?        S    21:21   0:00 /usr/lib/gimp/2
agrieser 21377 15.3  1.3  32548 13656 ?        Sl   21:32   0:00 gnome-terminal
agrieser 21378  0.0  0.0   2284   680 ?        S    21:32   0:00 gnome-pty-helpe
agrieser 21379  6.0  0.3   5676  3316 pts/0    Ss   21:32   0:00 bash
agrieser 21397  0.0  0.0   2396  1020 pts/0    R+   21:32   0:00 ps aux


I don't see it in there.
Programs that I was using at the time:
firefox
Xmms
Gimp
Gaim
Thunderbird

---

### Post by Pobega on 2007-01-01
I'm probably jumping to a conclusion, but what is located in these folders?

> agrieser 5901 0.0 0.1 4184 1692 ? S 14:24 0:00 /bin/sh /usr/bi

**Edit:** Nevermind, I jumped to thinking "bittorrent", I forgot about /usr/bin. I'll look through the list again

**Edit2:** Looking through ps' manual, 

*ps -e*

may work better. Sorry for wasting your time with the first command.

---

### Post by Atreus12 on 2007-01-01
I guess I was just wondering if other people had this happen as well. Before Ubuntu, I had never used bittorrent before. I don't know how it works, does it run all the time, or just when you start it?

I just didn't want my computer uploading a bunch of files on bittorent with my knowledge.

Here is ps -e

> 
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
  109 ?        00:00:00 pdflush
  112 ?        00:00:00 aio/0
  111 ?        00:00:00 kswapd0
  700 ?        00:00:00 kseriod
 1869 ?        00:00:00 ata/0
 1870 ?        00:00:00 ata_hotplug/0
 1874 ?        00:00:00 scsi_eh_0
 1875 ?        00:00:00 scsi_eh_1
 1896 ?        00:00:00 khubd
 1915 ?        00:00:00 khpsbpkt
 1949 ?        00:00:00 knodemgrd_0
 2051 ?        00:00:00 kjournald
 2284 ?        00:00:00 udevd
 3100 ?        00:00:00 shpchpd_event
 3268 ?        00:00:00 kgameportd
 3687 ?        00:00:00 kjournald
 3688 ?        00:00:01 kjournald
 3800 ?        00:00:00 wrap_wq
 3801 ?        00:00:07 ndis_wq
 4162 ?        00:00:00 acpid
 4292 ?        00:00:00 dd
 4294 ?        00:00:00 klogd
 4609 ?        00:00:00 gdm
 4638 ?        00:00:00 gdm
 4647 tty7     00:13:44 Xorg
 4648 ?        00:00:00 hpiod
 4655 ?        00:00:00 python
 4745 ?        00:00:00 dbus-daemon
 4760 ?        00:00:01 hald
 4761 ?        00:00:00 hald-runner
 4766 ?        00:00:00 hald-addon-acpi
 4816 ?        00:00:00 hald-addon-keyb
 4833 ?        00:00:03 hald-addon-stor
 4834 ?        00:00:03 hald-addon-stor
 4836 ?        00:00:03 hald-addon-stor
 4837 ?        00:00:02 hald-addon-stor
 4864 ?        00:00:00 dhcdbd
 4881 ?        00:00:00 NetworkManager
 4895 ?        00:00:00 NetworkManagerD
 4919 ?        00:00:00 hddtemp
 5061 ?        00:00:00 nmbd
 5063 ?        00:00:00 smbd
 5109 ?        00:00:00 smbd
 5125 ?        00:00:00 ntpd
 5143 ?        00:00:00 ntpd
 5144 ?        00:00:00 hcid
 5151 ?        00:00:00 sdpd
 5162 ?        00:00:00 krfcommd
 5177 ?        00:00:00 mdadm
 5217 ?        00:00:00 atd
 5236 ?        00:00:00 cron
 5352 tty1     00:00:00 getty
 5358 tty2     00:00:00 getty
 5361 tty3     00:00:00 getty
 5364 tty4     00:00:00 getty
 5367 tty5     00:00:00 getty
 5370 tty6     00:00:00 getty
 5434 ?        00:00:00 wpa_supplicant
 5464 ?        00:00:00 dhclient3
 5609 ?        00:00:00 gconfd-2
 5625 ?        00:00:00 x-session-manag
 5667 ?        00:00:00 ssh-agent
 5670 ?        00:00:00 dbus-daemon
 5671 ?        00:00:00 dbus-launch
 5674 ?        00:00:00 gnome-keyring-d
 5676 ?        00:00:00 bonobo-activati
 5678 ?        00:00:00 esd
 5680 ?        00:00:05 gnome-settings-
 5691 ?        00:02:04 metacity
 5697 ?        00:00:54 gnome-panel
 5699 ?        00:00:43 nautilus
 5706 ?        00:00:00 .conky_start.sh
 5708 ?        00:00:01 update-notifier
 5712 ?        00:00:00 gnome-volume-ma
 5716 ?        00:00:00 gnome-vfs-daemo
 5732 ?        00:00:01 trashapplet
 5740 ?        00:00:02 gnome-cups-icon
 5744 ?        00:00:00 gnome-power-man
 5746 ?        00:00:00 mapping-daemon
 5749 ?        00:00:00 clock-applet
 5751 ?        00:00:00 mixer_applet2
 5754 ?        00:01:44 conky
 5786 ?        00:00:07 gnome-screensav
 6017 ?        00:00:01 cupsd
 6030 ?        00:00:00 nessusd
 6188 ?        00:00:00 syslogd
 6300 ?        00:00:00 pdflush
 6671 ?        00:03:13 firefox-bin
23174 ?        00:00:00 gnome-terminal
23175 ?        00:00:00 gnome-pty-helpe
23176 pts/0    00:00:00 bash
23196 pts/0    00:00:00 ps


---

### Post by Pobega on 2007-01-01
Well as far as I know none of your clients are running in the background, do you have any of them set to autostart with GNOME? Settings > Sessions > Autostart (Or something similar) and check if there is anything torrent related there.

---

### Post by Atreus12 on 2007-01-02
> **Pobega said:**
> Well as far as I know none of your clients are running in the background, do you have any of them set to autostart with GNOME? Settings > Sessions > Autostart (Or something similar) and check if there is anything torrent related there.

Nope. Thanks for the help though, now I know how to keep an eye on it.

-Andrew

---

