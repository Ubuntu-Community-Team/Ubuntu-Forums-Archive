---
title: "Big wad of tasks?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Steve Baker on 2006-10-20
This may be a silly question but I've seen reference to the use of TOP in here several times and the list of tasks seemed pretty normal to me.  When I run TOP I get the following!:

[INDENT][FONT="Courier New"]top - 06:10:26 up  4:45,  2 users,  load average: 0.38, 0.43, 0.39
Tasks:  80 total,   1 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6% us,  0.3% sy,  0.0% ni, 92.1% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    321252k total,   305308k used,    15944k free,    14144k buffers
Swap:   353388k total,    77564k used,   275824k free,   161216k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4282 root      15   0 64272  20m 6620 S  3.6  6.6  14:44.96 Xorg
29494 stefan    15   0 55016  16m 9696 S  2.6  5.3   0:11.44 gnome-terminal
 5056 root      15   0 57236  14m 6988 S  0.7  4.6   2:43.47 firestarter
29532 stefan    16   0  2196 1108  856 R  0.7  0.3   0:01.53 top
 5051 stefan    16   0 45892 5888 5140 S  0.3  1.8   0:26.59 gnome-cups-icon
    1 root      16   0  1564  524  460 S  0.0  0.2   0:03.51 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.26 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   98 root      15   0     0    0    0 S  0.0  0.0   0:00.11 pdflush
   99 root      15   0     0    0    0 S  0.0  0.0   0:00.11 pdflush
  101 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  100 root      15   0     0    0    0 S  0.0  0.0   0:00.71 kswapd0
  688 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1811 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1881 root      15   0     0    0    0 S  0.0  0.0   0:00.66 kjournald
 2110 root      15  -4  2424  872  368 S  0.0  0.3   0:00.64 udevd
 2906 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 2919 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3118 dhcp      14  -2  2336  824  532 S  0.0  0.3   0:00.02 dhclient3
 3843 root      16   0  2156 1188  636 S  0.0  0.4   0:00.02 acpid
 4262 root      16   0 10908 1712 1232 S  0.0  0.5   0:00.01 gdm
 4269 root      15   0 11260 2356 1868 S  0.0  0.7   0:03.36 gdm
 4288 root      18   0  4712  904  788 S  0.0  0.3   0:00.00 hpiod
 4294 root      15   0  8280 4436 1076 S  0.0  1.4   0:00.53 python
 4381 clamav    18   0 28456  15m  860 S  0.0  5.0   0:15.12 clamd
 4439 clamav    15   0  5220 1024  924 S  0.0  0.3   0:00.47 freshclam
 4455 messageb  16   0  2192  716  604 S  0.0  0.2   0:00.24 dbus-daemon
 4470 haldaemo  16   0  6736 1612 1280 S  0.0  0.5   0:03.39 hald
 4471 root      16   0  2720  772  768 S  0.0  0.2   0:00.05 hald-runner
 4476 haldaemo  16   0  2000  664  660 S  0.0  0.2   0:00.00 hald-addon-acpi
 4526 haldaemo  16   0  2004  684  660 S  0.0  0.2   0:00.04 hald-addon-keyb
 4537 haldaemo  16   0  2008  776  728 S  0.0  0.2   0:00.97 hald-addon-stor
 4538 haldaemo  16   0  2004  796  728 S  0.0  0.2   0:01.16 hald-addon-stor
 4540 haldaemo  16   0  2004  792  728 S  0.0  0.2   0:01.20 hald-addon-stor
 4541 haldaemo  16   0  2004  700  684 S  0.0  0.2   0:01.16 hald-addon-stor
 4799 root      18   0  1968  520  516 S  0.0  0.2   0:00.00 hcid
 4803 root      18   0  1612  340  336 S  0.0  0.1   0:00.00 sdpd
 4818 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4831 root      16   0  1624  264  232 S  0.0  0.1   0:00.00 mdadm
 4936 root      16   0  1560  412  412 S  0.0  0.1   0:00.00 getty
 4937 root      16   0  1564  412  412 S  0.0  0.1   0:00.00 getty
 4938 root      16   0  1564  412  412 S  0.0  0.1   0:00.00 getty
 4939 root      16   0  1560  412  412 S  0.0  0.1   0:00.00 getty
 4940 root      16   0  1564  412  412 S  0.0  0.1   0:00.00 getty
 4941 root      16   0  1564  412  412 S  0.0  0.1   0:00.00 getty
 4955 root      15   0  4040  288  264 S  0.0  0.1   0:00.05 aplay
 4956 stefan    15   0 37780  13m 7632 S  0.0  4.4   0:04.50 x-session-manag
 4998 stefan    16   0  4336  448  416 S  0.0  0.1   0:00.00 ssh-agent
 5001 stefan    16   0  2708  516  512 S  0.0  0.2   0:00.00 dbus-launch
 5002 stefan    16   0  2192  864  748 S  0.0  0.3   0:00.02 dbus-daemon
 5004 stefan    16   0  6156 2880 1732 S  0.0  0.9   0:01.88 gconfd-2
 5007 stefan    19   0  2340  508  504 S  0.0  0.2   0:00.01 gnome-keyring-d
 5009 stefan    16   0  6392 2648 2016 S  0.0  0.8   0:00.66 bonobo-activati
 5011 stefan    15   0 27584 6444 5604 S  0.0  2.0   0:03.89 gnome-settings-
 5015 stefan    15   0  6320 1652 1264 S  0.0  0.5   5:56.62 esd
 5023 stefan    16   0 15540 8780 5960 S  0.0  2.7   0:50.21 metacity
 5030 stefan    15   0 51812  18m  12m S  0.0  6.0   0:29.14 gnome-panel
 5032 stefan    15   0 75760  13m 9580 S  0.0  4.2   0:08.82 nautilus
 5035 stefan    16   0 17124 4276 3740 S  0.0  1.3   0:00.72 gnome-volume-ma
 5041 stefan    15   0 33784 7372 6184 S  0.0  2.3   0:02.87 update-notifier
 5044 stefan    15   0  8480 2860 2464 S  0.0  0.9   0:00.74 gnome-vfs-daemo
 5046 stefan    15   0 29656 5144 5120 S  0.0  1.6   0:02.22 gksu
 5060 stefan    15   0 17712 4568 3808 S  0.0  1.4   0:01.47 gnome-power-man
 5062 stefan    15   0 40140 6768 5176 S  0.0  2.1   0:01.45 trashapplet
 5071 stefan    16   0  2280  720  688 S  0.0  0.2   0:00.01 mapping-daemon
 5087 stefan    16   0 23420 9056 6152 S  0.0  2.8   0:02.07 clock-applet
 5089 stefan    15   0 34872  10m 6964 S  0.0  3.4   0:03.96 mixer_applet2
 5092 stefan    15   0 14612 2412 1828 S  0.0  0.8   0:05.55 gnome-screensav
 5104 root      16   0  6044 3496 1740 S  0.0  1.1   0:01.01 gconfd-2
 5108 root      16   0  3084 1292 1044 S  0.0  0.4   0:00.05 esd
 5656 cupsys    26  10  4340 1872 1292 S  0.0  0.6   0:07.10 cupsd
stefan@stefan-desktop:~$[/FONT][/INDENT]

Is this normal?  I see some things repeated a number of times.  80 tasks? 79 are sleeping?  :-? 

Also, it says 2 users -- as far as I know, I'm alone here. :???: 

Thanks for the help  :) You see I think I may have over-done it sampling applications.  :redface:

Stefan

---

### Post by chuckyp on 2006-10-20
Looks okay to me.

---

### Post by PriceChild on 2006-10-20
The 2 users is because you're logged into your x session on tty7, and also into a terminal inside that.

Everything is fine :)

---

### Post by mthaddon on 2006-10-20
Yep, all looks good. The columns to watch particularly are CPU% and Mem% - this tells you how CPU and Memory is being used by each application (obviously). By default "top" orders by CPU usage. If you open up a bunch more applications and run top again, you can see which ones are taking up the most resources. 

Here's mine for comparison:

```
top - 13:24:14 up 1 day,  1:08,  3 users,  load average: 0.14, 0.19, 0.25
Tasks: 156 total,   1 running, 154 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.3% us,  0.8% sy,  0.0% ni, 96.8% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1025092k total,   845748k used,   179344k free,    16492k buffers
Swap:  3012148k total,   371604k used,  2640544k free,   182488k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4616 root      15   0  539m 168m  11m S    3 16.8 289:05.00 Xorg-air
 8312 mthaddon  15   0 75540  16m 9316 S    2  1.6   0:10.42 gnome-terminal
16579 mthaddon  16   0  2196 1152  856 R    1  0.1   0:00.02 top
 4265 messageb  15   0  2324  848  660 S    0  0.1   0:25.87 dbus-daemon
    1 root      16   0  1564  468  444 S    0  0.0   0:02.53 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.32 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/1
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread
   14 root      10  -5     0    0    0 S    0  0.0   0:18.60 kblockd/0
   15 root      10  -5     0    0    0 S    0  0.0   0:00.98 kblockd/1
   16 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid
  119 root      15   0     0    0    0 S    0  0.0   0:11.29 pdflush
  121 root      15   0     0    0    0 S    0  0.0   1:03.86 kswapd0
  122 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  123 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  719 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  804 root      15   0     0    0    0 S    0  0.0   0:00.02 kirqd
 1804 root      14  -5     0    0    0 S    0  0.0   0:00.00 ata/0
 1805 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1
 1806 root      14  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/0
 1807 root      14  -5     0    0    0 S    0  0.0   0:00.00 ata_hotplug/1
 1812 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
 1813 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 1879 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2003 root      16   0     0    0    0 S    0  0.0   0:18.02 kjournald
 2272 root      12  -4  2428  420  364 S    0  0.0   0:00.28 udevd
 3085 root      20   0     0    0    0 S    0  0.0   0:00.00 shpchpd_event
 3271 root      15   0     0    0    0 S    0  0.0   0:00.00 cifsoplockd
 3272 root      15   0     0    0    0 S    0  0.0   0:00.00 cifsdnotifyd
 3683 root      15   0     0    0    0 S    0  0.0   0:00.05 cifsd
 4106 root      16   0  2156  616  616 S    0  0.1   0:00.00 acpid
 4244 root      16   0  1680  408  388 S    0  0.0   0:00.05 dd
 4246 klog      16   0  2408  432  384 S    0  0.0   0:00.07 klogd
 4280 haldaemo  15   0  6872 1848 1356 S    0  0.2   0:36.16 hald
 4281 root      18   0  2716  792  788 S    0  0.1   0:00.02 hald-runner
 4286 haldaemo  17   0  2008  672  668 S    0  0.1   0:00.00 hald-addon-acpi

```

I have Evolution, Firefox, Liferea, Nautilus, Thunderbird, Tomboy, and Gnome-Terminal running. Can't see them all in the list because they aren't using resources at this snapshot, but there you have it. You can change the order by typing "O" and then the letter corresponding to the column you want to sort by and Enter. Or you can filter by user: type "u" and then your username - this will filter out any other processes (most likely those owned by root).

For diagnosing memory usage issues, try "free -m" the "Free" column in the second row ("-/+ buffers/cache") will tell you how much free memory you have.

Cheers, Tom

---

### Post by Steve Baker on 2006-11-02
Thanks all - been distracted for a little while.  :-D 

Steve

---

### Post by Steve Baker on 2006-11-02
Umm.  Please humor me for a bit.  :???:   Maybe I'm too analytical but I am still confused by things being repeated in the list like 'hald-addon-stor' and 'getty'  Where can I look up what these tasks do and what programs use them?

Steve

---

