---
title: "100% CPU Usage (kacpi-work)"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by AndyNguyen on 2007-03-14
I just did a fresh install of Ubuntu from a Live CD.  I am getting 100% CPU usage and it's really bogging the system down.  Freezing for 2-3 seconds every 30 seconds or so.  The culprits are kacpi-work-0 and kacpi-work-1, combined it takes up all the usage.  This is the output when I use the top command.

```
top - 20:40:14 up 14 min,  2 users,  load average: 4.11, 3.71, 2.25
Tasks:  93 total,   4 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.8% us, 90.7% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.5% hi,  0.0% si
Mem:   1035904k total,   307980k used,   727924k free,     6740k buffers
Swap:  1028152k total,        0k used,  1028152k free,   167492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  996 root      20  -5     0    0    0 R 81.8  0.0  11:35.39 kacpid-work-0
 1004 root      10  -5     0    0    0 S  9.3  0.0   1:56.35 kacpid-work-1
 5026 andy      15   0 32172  13m 8328 S  6.4  1.3   0:00.95 gnome-terminal
 4257 root      15   0 52384  25m  10m S  2.1  2.5   0:08.95 Xorg
 4680 andy      15   0 15280 9140 6448 S  0.5  0.9   0:01.15 metacity
    1 root      16   0  1564  524  460 S  0.0  0.1   0:01.10 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kacpid
  165 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  166 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  168 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  167 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  757 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1858 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1877 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1907 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 1993 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 2223 root      12  -4  2432  924  368 S  0.0  0.1   0:00.13 udevd
 2991 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3029 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 hda_codec/0
 3070 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3090 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ipw2200/0
 3304 dhcp      14  -2  2332  560  264 S  0.0  0.1   0:00.00 dhclient3
 3545 root      10  -5     0    0    0 S  0.0  0.0   0:06.56 kacpid-work-2
 3595 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3632 dhcp      14  -2  2332  756  460 S  0.0  0.1   0:00.00 dhclient3
 4000 root      16   0  2156 1196  644 S  0.0  0.1   0:00.00 acpid
 4088 syslog    16   0  1764  672  548 S  0.0  0.1   0:00.00 syslogd
 4114 root      16   0  1684  500  412 S  0.0  0.0   0:00.01 dd
 4116 klog      17   0  2392 1312  388 S  0.0  0.1   0:00.05 klogd
 4135 messageb  17   0  2196  852  668 S  0.0  0.1   0:00.04 dbus-daemon
 4150 haldaemo  16   0  6876 5480 1564 S  0.0  0.5   0:01.08 hald
 4151 root      16   0  2716  992  848 S  0.0  0.1   0:00.00 hald-runner
 4156 haldaemo  16   0  2004  796  696 S  0.0  0.1   0:00.00 hald-addon-acpi
 4206 haldaemo  15   0  2004  792  692 S  0.0  0.1   0:00.01 hald-addon-keyb
 4216 haldaemo  16   0  2012  820  716 R  0.0  0.1   0:00.01 hald-addon-stor
 4217 haldaemo  16   0  2012  820  716 S  0.0  0.1   0:00.02 hald-addon-stor
 4246 root      15   0 10912 1792 1220 S  0.0  0.2   0:00.00 gdm
 4247 root      16   0 11264 2548 1912 S  0.0  0.2   0:00.00 gdm
 4290 hplip     16   0 12876  920  696 S  0.0  0.1   0:00.00 hpiod
 4293 hplip     15   0  9408 4668 1096 S  0.0  0.5   0:00.00 python
 4340 cupsys    16   0  4204 1792 1300 S  0.0  0.2   0:00.01 cupsd
 4385 root      21   5  1556  264  192 R  0.0  0.0   0:00.01 powernowd

```

---

### Post by Skia_42 on 2007-03-14
How fast is your hardware? (RAM, CPU, etc.) The requirments for [Xubuntu]("http://xubuntu.com/") are less then Ubuntu, it is probably an option worth checking out.

---

### Post by AndyNguyen on 2007-03-14
1 gig of RAM, 1.8 ghz Mobile Centrino

---

### Post by HellSpawn on 2007-03-31
Have you tried uninstalling KACPI??

Use "sensors-detect" and "sensors" to see the Temperture of your CPU and the RPM of your FANS.
Maybe your burning your CPU.

The 100% issue is not really the problem, but the Load Average your TOP is displaying is.

What brand is this laptop??

See ya...

---

