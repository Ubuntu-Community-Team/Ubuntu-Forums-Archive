---
title: "100% CPU Use?? Xorg??"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by jms830 on 2006-03-01
Why does my computer have 100% cpu use?
I did some research and i think it is Xorg that is doing it.

here is what i get when i type "top"

top - 12:29:08 up 16:08,  3 users,  load average: 1.06, 1.14, 1.01
Tasks:  85 total,   2 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 92.7% us,  7.3% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1035992k total,   981436k used,    54556k free,    76992k buffers
Swap:  1004052k total,    12532k used,   991520k free,   494500k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8943 root      25   0  237m  86m  10m R 91.6  8.6  45:14.30 Xorg
22497 jordan    15   0  101m  39m  17m S  2.7  3.9   0:42.66 firefox-bin
22341 jordan    15   0 32384  14m 9.9m S  2.3  1.5   0:07.13 gnome-terminal
22640 jordan    15   0  2676  992  784 S  2.3  0.1   0:11.10 xrestop
22732 jordan    16   0  2136 1088  844 R  0.3  0.1   0:00.28 top
    1 root      16   0  1560  528  460 S  0.0  0.1   0:01.37 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   67 root      10  -5     0    0    0 S  0.0  0.0   0:00.39 kblockd/0
   93 root      15   0     0    0    0 S  0.0  0.0   0:00.24 pdflush
   94 root      15   0     0    0    0 S  0.0  0.0   0:00.72 pdflush
   96 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   95 root      15   0     0    0    0 S  0.0  0.0   0:02.41 kswapd0
  681 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod

and when i type "xrestop"

xrestop - Display: localhost:0
          Monitoring 25 clients. XErrors: 0
          Pixmaps:   20864K total, Other:    2962K total, All:   23827K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
3000000   151   34    1 108712 108760     4233K   2554K   6788K   ?   Fallendoom2c00000   105   26    1  269  317     3877K     11K   3888K   ?   jordan@ubuntu:3a00000     0    0    0    1    0     3072K      0B   3072K   ?   <unknown>
1e00000   144   39    1  378   77     2541K      7K   2548K   ?   Ubuntu Forums
1200000    52   43    1 8874 8925     1042K    212K   1254K  9438 Desktop
0e00000   177   40    1 2543 2582      958K     66K   1024K  9436 Drawer
1a00000    39   36    0  497  522      817K     13K    831K  9436 wnck-applet
0c00000    14   27    2  191  963      786K     25K    812K  9427 metacity
1c00000    10   28    0  280  283      406K      7K    413K  9436 mixer_applet2
2000000     5   26    0  135  134      403K      3K    407K  9436 trashapplet
1400000    10   26    0  252  261      392K      6K    399K  9436 update-notifie2600000    11   32    0  135  143      393K      4K    398K  9436 multiload-appl2200000     9   26    0  137  145      388K      4K    392K  9436 notification-a2a00000     8   32    0  134  143      388K      4K    392K  9436 clock-applet
2800000     5   26    0  133  142      388K      4K    392K  9436 gweather-apple2400000     8   26    0  131  137      388K      4K    392K  9436 gnome-netstatu0600000     2    2    0    2    9      384K    312B    384K  9342 gnome-session
0a00000     1    1    0    0  770        0B     18K     18K   ?   screensaver
0800000     7   22    0    1  441        4B     11K     11K  9395 gnome-settings

---

### Post by jms830 on 2006-03-01
ok i closed GAIM and i fixed it... but still does anyone know why this is happening/ how to fix it?

---

### Post by WelterPelter on 2006-03-01
Are you running folding@home? That will keep your CPU usage constantly at 100%.

---

### Post by jms830 on 2006-03-01
I don't know what folding@home is or if i am running it.

---

