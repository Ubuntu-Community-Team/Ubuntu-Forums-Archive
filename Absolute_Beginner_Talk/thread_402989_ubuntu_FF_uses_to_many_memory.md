---
title: "ubuntu FF uses to many memory"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-04-06
hi.
i've recently installed a Feisty Beta on my laptop.
i'm using IceWM as my main window manager. ive added some gnome-based programms to my ./icewm/startup file 

#!/bin/bash
gnome-settings-daemon &
gnome-power-manager &

i run free -m command and thats what i get :

szymon@linugrat:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026       1919        106          0          0       1754
-/+ buffers/cache:        164       1861
Swap:          337         25        311

and thats my top : 

top - 17:37:55 up 14:31,  1 user,  load average: 0.06, 0.11, 0.09
Tasks: 113 total,   2 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2074628k total,  1969020k used,   105608k free,       36k buffers
Swap:   345388k total,    26076k used,   319312k free,  1796916k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5343 root      15   0  296m  19m 3796 S    0  1.0   5:55.77 Xorg
 7649 szymon    15   0  2320 1172  880 R    0  0.1   0:00.06 top
 7653 szymon    15   0 33648 8468 4852 S    0  0.4   0:00.01 gvim
    1 root      18   0  2912 1848  524 S    0  0.1   0:01.03 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    8 root      10  -5     0    0    0 S    0  0.0   0:00.31 events/0
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread
   35 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   36 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   37 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   38 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  179 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  208 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush
  209 root      15   0     0    0    0 S    0  0.0   0:01.17 pdflush
  210 root      10  -5     0    0    0 S    0  0.0   0:00.53 kswapd0
  211 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  212 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  850 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd
 2101 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 2102 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2182 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 2275 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0
 2287 root      10  -5     0    0    0 S    0  0.0   0:09.18 ata/0
 2288 root      10  -5     0    0    0 S    0  0.0   0:00.05 ata/1
 2289 root      13  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 2305 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
 2306 root      10  -5     0    0    0 S    0  0.0   0:16.76 scsi_eh_1
 2516 root      10  -5     0    0    0 S    0  0.0   0:00.12 xfslogd/0
 2517 root      10  -5     0    0    0 S    0  0.0   0:00.00 xfslogd/1
 2518 root      10  -5     0    0    0 S    0  0.0   0:00.35 xfsdatad/0
 2520 root      13  -5     0    0    0 S    0  0.0   0:00.00 xfsdatad/1
 2522 root      10  -5     0    0    0 S    0  0.0   0:00.00 xfsbufd
 2524 root      10  -5     0    0    0 S    0  0.0   0:00.00 xfssyncd
 2683 root      14  -4  2888 1232  376 S    0  0.1   0:00.29 udevd
 3674 root      16  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused
                                                                                                 

so depsite having 2 gb of ram, my linux still uses a swap :-/
any question why? swapping is a little annoying :/

---

### Post by dstew on 2007-04-06
It looks like your processes are not using that memory. Maybe some hardware or driver is using it.

---

### Post by heimo on 2007-04-06
Your system is using about 25MB of swap. That's very, very little. If you think that's a problem, you can always disable swap.

>               total       used       free     shared    buffers     cached
Mem:          2026       1919        106          0          0       1754
-/+ buffers/cache:        164       1861
Swap:          337         25        311

---

### Post by Obor on 2007-04-06
You can change the swappiness if you don't like using swap. [Little article about memory management here]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

The default value for vm.swappiness is 60 in Ubuntu Feisty which is a good default value but if you want to tweak the performance a little bit more you can change this value to a lower value to reduce the load of the swap.

To change the value permanently you need to change the sysctl.conf file:
```
gksudo gedit /etc/sysctl.conf
```
Add the line
```
vm.swappiness=10
```
To the end of the file. This way it will be set upon boot. 

i.e I use value of 20 on my laptop with 512MB RAM

Source: [here>>]("http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html")

---

### Post by szymon_g on 2007-04-06
thanks for answers
btw, on the same laptop, on Edgy i had never used more than 1-1.2 gb of memory (in first mem line, not +/- buffer)not to mention that i've never used a swap :-/
and now- all memory is used. processess were default, icewm + gnome-settings :-/

---

### Post by heimo on 2007-04-06
On the outputs you quoted, your system has about 1.8GB of the memory allocated for disk cache (to speed up disk use), which can be freed for applications, if neccessary. It's a lot better to use the memory than have it unused. This is commonly misunderstood as a bad thing.

---

### Post by szymon_g on 2007-04-06
ok, but why it uses a swap? i'm not a specialist, but imho if it allocate so many memory for it shouldn't use swap  :-> especially when i'm not using computer hardly (i.e. i'm not video-editing etc)

---

### Post by heimo on 2007-04-06
Probably because there is some kind of algorithm, which mathematically tries to optimize memory usage and swapping in a way that makes your system as fast as possible. It may work or it may not work, I guess it's not a trivial problem. Start reading here:
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

