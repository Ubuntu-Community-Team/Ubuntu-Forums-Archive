---
title: "MEM use?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by timbosity on 2008-02-26
running Xubuntu on 256 RAM (as far I know...)
just wondering why when I run nothing im still using ~40-50% ram. Is that what xorg, xfce4-desktop etc uses???
Here is output from top with firefox pidgin and Terminal open:

top - 08:59:26 up 46 min,  2 users,  load average: 0.04, 0.28, 0.29
Tasks:  89 total,   2 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  2.7%sy,  0.0%ni, 88.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    223428k total,   219356k used,     4072k free,     3772k buffers
Swap:   377488k total,    34684k used,   342804k free,    74932k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4735 root      15   0  284m  20m 7664 S  6.0  9.5   1:50.74 Xorg               
 6461 tim       15   0 75620  19m  10m R  4.3  8.9   0:01.32 xfce4-terminal     
 6445 tim       15   0  143m  46m  20m S  1.0 21.1   0:20.10 firefox-bin        
 5258 tim       15   0 10244 3816 3068 S  0.7  1.7   0:19.07 conky              
 5260 tim       15   0 10240 3804 3064 S  0.7  1.7   0:18.06 conky              
 6480 tim       15   0  2360 1132  876 R  0.7  0.5   0:00.45 top                
    1 root      18   0  2952 1852  532 S  0.0  0.8   0:01.43 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  111 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod          

this is output from ps -aux without anything running (actually pidgin was running):

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.8   2952  1852 ?        Ss   08:12   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   08:12   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   08:12   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   08:12   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   08:12   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   08:12   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   08:12   0:00 [khelper]
root        26  0.0  0.0      0     0 ?        S<   08:12   0:00 [kblockd/0]
root        27  0.0  0.0      0     0 ?        S<   08:12   0:00 [kacpid]
root        28  0.0  0.0      0     0 ?        S<   08:12   0:00 [kacpi_notify]
root       111  0.0  0.0      0     0 ?        S<   08:12   0:00 [kseriod]
root       132  0.0  0.0      0     0 ?        S    08:12   0:00 [pdflush]
root       133  0.0  0.0      0     0 ?        S    08:12   0:00 [pdflush]
root       134  0.0  0.0      0     0 ?        S<   08:12   0:00 [kswapd0]
root       186  0.0  0.0      0     0 ?        S<   08:12   0:00 [aio/0]
root      1926  0.0  0.0      0     0 ?        S<   08:12   0:00 [ata/0]
root      1927  0.0  0.0      0     0 ?        S<   08:12   0:00 [ata_aux]
root      1943  0.0  0.0      0     0 ?        S<   08:12   0:00 [ksuspend_usbd]
root      1944  0.0  0.0      0     0 ?        S<   08:12   0:00 [khubd]
root      2264  0.0  0.0      0     0 ?        S<   08:12   0:00 [kjournald]
root      2455  0.0  0.5   2960  1308 ?        S<s  08:12   0:00 /sbin/udevd --d
root      3255  0.0  0.0      0     0 ?        S<   08:12   0:00 [pccardd]
root      3278  0.0  0.0      0     0 ?        S<   08:12   0:00 [pccardd]
root      3334  0.0  0.0      0     0 ?        S<   08:12   0:00 [kpsmoused]
root      3426  0.0  0.0      0     0 ?        S<   08:12   0:00 [kgameportd]
root      3927  0.0  0.2   1692   512 tty4     Ss+  08:13   0:00 /sbin/getty 384
root      3928  0.0  0.2   1692   516 tty5     Ss+  08:13   0:00 /sbin/getty 384
root      3932  0.0  0.2   1696   520 tty2     Ss+  08:13   0:00 /sbin/getty 384
root      3933  0.0  0.2   1696   516 tty3     Ss+  08:13   0:00 /sbin/getty 384
root      3934  0.0  0.2   1692   512 tty1     Ss+  08:13   0:00 /sbin/getty 384
root      3935  0.0  0.2   1692   512 tty6     Ss+  08:13   0:00 /sbin/getty 384
root      4131  0.0  0.5   2432  1316 ?        Ss   08:13   0:00 /usr/sbin/acpid
root      4181  0.0  0.0      0     0 ?        S<   08:13   0:00 [kondemand/0]
syslog    4234  0.0  0.3   1916   736 ?        Ss   08:13   0:00 /sbin/syslogd -
root      4290  0.0  0.2   1836   532 ?        S    08:13   0:00 /bin/dd bs 1 if
klog      4292  0.0  0.6   2496  1400 ?        Ss   08:13   0:00 /sbin/klogd -P
105       4313  0.0  0.4   2908  1068 ?        Ss   08:13   0:00 /usr/bin/dbus-d
root      4329  0.0  0.9  12556  2040 ?        Ssl  08:13   0:00 /usr/sbin/Netwo
root      4343  0.0  0.5   3276  1284 ?        Ss   08:13   0:00 /usr/sbin/Netwo
root      4356  0.0  0.3   3084   812 ?        Ss   08:13   0:00 /usr/bin/system
root      4357  0.0  0.5   2772  1256 ?        S    08:13   0:00 dbus-daemon --s
108       4376  0.0  1.6   5632  3684 ?        Ss   08:13   0:00 /usr/sbin/hald
root      4377  0.0  0.4   3096  1028 ?        S    08:13   0:00 hald-runner
108       4432  0.0  0.3   2156   892 ?        S    08:13   0:00 hald-addon-keyb
108       4436  0.0  0.3   2156   888 ?        S    08:13   0:00 hald-addon-keyb
108       4437  0.0  0.3   2160   892 ?        S    08:13   0:00 hald-addon-keyb
root      4440  0.0  0.4   3156   980 ?        S    08:13   0:00 /usr/lib/hal/ha
108       4442  0.0  0.3   2160   880 ?        S    08:13   0:00 hald-addon-acpi
108       4447  0.0  0.3   2160   892 ?        S    08:13   0:00 hald-addon-keyb
root      4470  0.0  1.2   6036  2684 ?        Ss   08:13   0:00 /usr/sbin/cupsd
108       4509  0.0  0.5   3264  1188 ?        S    08:13   0:00 hald-addon-stor
avahi     4659  0.0  0.6   2728  1364 ?        Ss   08:13   0:00 avahi-daemon: r
avahi     4660  0.0  0.2   2728   452 ?        Ss   08:13   0:00 avahi-daemon: c
root      4689  0.0  0.3   1992   892 ?        Ss   08:13   0:00 /usr/sbin/dhcdb
root      4725  0.0  0.8  13096  1932 ?        Ss   08:13   0:00 /usr/sbin/gdm -
root      4728  0.0  1.2  13516  2860 ?        S    08:13   0:00 /usr/sbin/gdm -
root      4735  3.7  8.8  26492 19688 tty7     Ss+  08:13   1:29 /usr/bin/X :0 -
daemon    4786  0.0  0.1   1956   424 ?        Ss   08:13   0:00 /usr/sbin/atd
root      4800  0.0  0.4   2332   912 ?        Ss   08:13   0:00 /usr/sbin/cron
dhcp      4839  0.0  0.5   2416  1164 ?        S    08:13   0:00 /sbin/dhclient
tim       5180  0.0  4.0  35052  9124 ?        Ssl  08:22   0:00 x-session-manag
tim       5210  0.0  0.2   4436   540 ?        Ss   08:22   0:00 /usr/bin/ssh-ag
tim       5213  0.0  0.2   2700   632 ?        S    08:22   0:00 /usr/bin/dbus-l
tim       5214  0.0  0.4   2772  1008 ?        Ss   08:22   0:00 /usr/bin/dbus-d
tim       5219  0.0  2.2  30096  5092 ?        Ss   08:22   0:00 xfce-mcs-manage
tim       5221  0.0  0.4   5012   956 ?        S    08:22   0:00 gnome-keyring-d
tim       5223  0.0  1.2   5692  2864 ?        S    08:22   0:00 /usr/lib/libgco
tim       5224  0.0  3.9  17656  8844 ?        S    08:22   0:01 xfwm4 --sm-clie
tim       5226  0.0  5.4  62464 12160 ?        S    08:22   0:01 /usr/bin/xfdesk
tim       5228  0.0  0.4   2748  1116 ?        S    08:22   0:00 /usr/lib/gamin/
tim       5233  0.2  5.8  30488 13180 ?        S    08:22   0:03 /usr/X11R6/bin/
tim       5234  0.0  5.5  32984 12404 ?        S    08:22   0:00 update-notifier
tim       5235  0.0  4.8  28480 10772 ?        S    08:22   0:00 /usr/lib/xfdesk
tim       5241  0.0  5.2  22804 11696 ?        Ss   08:22   0:00 python /usr/sha
tim       5244  0.0  5.2  41360 11696 ?        Ss   08:22   0:00 nm-applet --sm-
tim       5245  0.0  4.1  24800  9168 ?        S    08:22   0:00 /usr/lib/xfce4-
tim       5246  0.0  4.6  29144 10280 ?        S    08:22   0:00 /usr/lib/xfce4/
tim       5253  0.0  2.9  24520  6580 ?        S    08:22   0:00 /usr/lib/thunar
tim       5255  0.0  0.4  33648   968 ?        Ssl  08:22   0:00 fusesmb /media/
tim       5258  0.8  1.7  10244  3816 ?        S    08:22   0:16 conky
tim       5260  0.8  1.7  10240  3804 ?        S    08:22   0:15 conky
tim       5265  0.0  2.0  13952  4584 ?        S    08:22   0:00 /usr/bin/Thunar
tim       5820  0.3  9.8  58348 22064 ?        Sl   08:38   0:03 pidgin
tim       6126 13.4  8.8  75488 19744 ?        Rs   08:53   0:01 xfce4-terminal
tim       6127  0.2  0.3   2664   740 ?        S    08:53   0:00 gnome-pty-helpe
tim       6128  8.0  1.4   5748  3136 pts/0    Ss   08:53   0:00 bash
tim       6145  0.0  0.4   2620  1004 pts/0    R+   08:53   0:00 ps -aux

Should I consider upgrading memory? I think my laptop can take up to 512 and there's a spare slot in there somewhere for an extra 256 card...

Suggestions for streamlining this baby and making a mean lean machine would be most welcome

EDIT: forgot to say what heavy apps I use mostly: openoffice, firefox, gimp (thats a real slow downer), etc...

---

### Post by lizzard on 2008-02-26
Try this command to get further info about your memory usage:
 ```
free -m 
```

---

### Post by timbosity on 2008-02-26
heres free -m output... what is it telling me??


             total       used       free     shared    buffers     cached
Mem:           218        202         16          0          1         57
-/+ buffers/cache:        143         74
Swap:          368         33        334

---

### Post by lizzard on 2008-02-26
> **timbosity said:**
> heres free -m output... what is it telling me??


             total       used       free     shared    buffers     cached
Mem:           218        202         16          0          1         57
-/+ buffers/cache:        143         74
Swap:          368         33        334

You see 57 MB are used for caching purposes. It means it's used to speed up your system, because the data stored as cache is read from RAM instead from harddrive when needed. The memory used by cache is available for programs, if they need it. They can free some cache for their own usage. So in fact you have 74 MB of memory available.

---

### Post by hyper_ch on 2008-02-26
unused ram is wasted ram...

---

### Post by timbosity on 2008-02-26
ok,

I understand about unused RAM being wasted RAM and that I should be looking at load averages instead, worrying if they rise to above 1 for any extensive periods of time. Still doesnt answer my question about whether or not I can improve the performance of those heavier apps??

---

### Post by hyper_ch on 2008-02-26
> **timbosity said:**
> Still doesnt answer my question about whether or not I can improve the performance of those heavier apps??

Sure you can... get a better cpu, more ram, faster harddisks, close applications you don't need...

---

### Post by timbosity on 2008-02-26
Right... thats very usefull.

thank you...

I was looking more for a "you dont need those things running in the background and this is how you go about making sure they only run when absolutely needed" im referring to for example python running at pid 5241 from ps -aux output

What would opinion be on upgrading RAM. As I said i think my laptop can take up to 512 with an extra 256 card. This would cost me around 78euro. I wouldnt really feel confident enough to upgrade cpu (AMD athlon 1600) and probably wouldnt need to (??) and 20GB HD is fine for what im doing. 
What i really want to know:

 is it worth the hassle/cost of getting the extra RAM?
 what kindof hassle is it ie what are the chances ill completely stuff up the thing?
 how much "extra" would it give my entire "computing experience"?

any experience/advice appreciated:popcorn:

---

