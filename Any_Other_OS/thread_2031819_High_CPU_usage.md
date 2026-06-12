---
title: "High CPU usage"
date: 2012-07-22
forum: Any Other OS
---

### Post by N3tMast3r on 2012-07-22
Hello,

I just installed Ubuntu 10.04 32-bit on my DELL Latitude D620 and the CPU usage is really high even when I do nothing. Both processors are never below 75% of usage. 

If I see the processes there is only firefox which is taking about 10%, compiz 2%, skype 3% gnome system monitor 8%, xorg 10% and then all the other processes 0%...

The computer is always slow due to high cpu usage... Even as soon as It starts. it often get stuck and it takes forever to open new firefox or opera tabs...

My laptopo:
dell latitude d620
centrino duo dual core 1.83Ghz
4GB ram
80GB hard drive

please help. 

Thank you!

---

### Post by ajgreeny on 2012-07-22
We really need to know what is using all the cpu, so run top in terminal and then type an upper case "P" to sort processes by processor usage %age.

This from **man top** shows what other sorting you can use.
```
SORTING of task window
         For  compatibility, this top supports most of the former top sort keys.  Since this is primarily a
         service to former top users, these commands do not appear on any help screen.
            command   sorted field                  supported
              A         start time (non-display)      No
              M         %MEM                          Yes
              N         PID                           Yes
              P         %CPU                          Yes
              T         TIME+                         Yes
```

---

### Post by N3tMast3r on 2012-07-22
Thanks for the reply. This is the output:

 ```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 1359 root      19  -1  317m  20m 9.9m S   17  0.6  68:25.65 Xorg                                                                                                                
27094 root      20   0 54548  21m  16m S   11  0.7 105:03.22 gnome-system-mo                                                                                                     
 1430 root      20   0  104m 101m 2212 S    9  3.1  43:40.76 gconfd-2                                                                                                            
27796 root      20   0 46860  13m  10m S    6  0.4   2:21.42 gnome-terminal                                                                                                      
 1422 root      20   0  3108 1252  624 S    6  0.0  27:47.52 dbus-daemon                                                                                                         
 4755 root      20   0  653m 289m  33m S    4  8.9  37:46.56 firefox-bin                                                                                                         
 1418 root      20   0 27516 8204 5352 S    3  0.2  12:07.85 x-session-manag                                                                                                     
 3301 root      20   0  382m  85m  20m S    3  2.6  16:19.37 skype                                                                                                               
 5875 root      20   0  178m  38m  17m R    2  1.2  18:29.92 plugin-containe                                                                                                     
 1461 root      20   0 94812  38m  15m S    2  1.2   9:00.43 compiz                                                                                                              
 1464 root      20   0 43644  16m  11m S    2  0.5   7:15.86 gnome-panel                                                                                                         
 1478 root      20   0 20580 7728 6216 S    1  0.2   5:12.57 gnome-power-man                                                                                                     
 1922 root      20   0 48776  12m   9m S    1  0.4   3:28.48 indicator-apple                                                                                                     
 1436 root      20   0 89252 9436 7320 S    1  0.3   4:42.53 gnome-settings-                                                                                                     
 1437 root      20   0 23988 2000 1596 S    1  0.1   2:08.24 gnome-keyring-d                                                                                                     
 1921 root      20   0 63316  15m  11m S    1  0.5   3:44.08 clock-applet                                                                                                        
 1985 root      20   0 85132 4504 3608 S    1  0.1   2:12.45 indicator-sound                                                                                                     
 1987 root      20   0 21192 7756 5884 S    1  0.2   3:10.65 notification-da                                                                                                     
 1991 root      20   0 24360 4244 3464 S    1  0.1   2:37.01 indicator-appli                                                                                                     
 1993 root      20   0 17060 3588 2896 S    1  0.1   2:15.32 indicator-messa                                                                                                     
30758 root      20   0  2596 1096  820 R    1  0.0   0:03.36 top                                                                                                                 
  890 messageb  20   0  2988 1216  664 S    0  0.0   1:26.67 dbus-daemon                                                                                                         
 1333 root      20   0 22572 6944 2168 S    0  0.2   2:50.18 wicd                                                                                                                
 1441 root      20   0  6428 2220 1892 S    0  0.1   2:08.10 gvfsd                                                                                                               
 1471 root      20   0 83492  15m  11m S    0  0.5   1:47.05 nautilus                                                                                                            
21406 root      20   0     0    0    0 S    0  0.0   0:02.32 kworker/0:3                                                                                                         
26878 root      20   0     0    0    0 S    0  0.0   0:13.73 kworker/1:1                                                                                                         
    1 root      20   0  2860 1660 1192 S    0  0.0   0:02.13 init                                                                                                                
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd                                                                                                            
    3 root      20   0     0    0    0 S    0  0.0   0:09.38 ksoftirqd/0                                                                                                         
    6 root      RT   0     0    0    0 S    0  0.0 371:19.08 migration/0                                                                                                         
    7 root      RT   0     0    0    0 S    0  0.0   0:00.38 watchdog/0                                                                                                          
    8 root      RT   0     0    0    0 S    0  0.0 304:06.27 migration/1                                                                                                         
   10 root      20   0     0    0    0 S    0  0.0   0:12.28 ksoftirqd/1                                                                                                         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.35 watchdog/1                                                                                                          
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                              
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                                                                                           
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                               
   17 root      20   0     0    0    0 S    0  0.0   0:00.18 sync_supers       
```

but then when I take a look at the "Resources" from the System Monitor, I see both the CPUs at about 80%-100% of usage. :( Even right after the computer starts.

Please help! I have the same distribution on another computer but 64 bits and I do not have this problem :(

---

### Post by ajgreeny on 2012-07-23
I can not understand the discrepancy between top and system-monitor, but I seldom, if ever use system-monitor as it alone takes quite a  lot of resources, but top almost none in comparison.

However, top shows xorg using 17% cpu, which is quite high; most of the time mine runs with xorg at about 1% - 2%, seldom rising above that in normal use.

What graphic card do you have, and what driver is it using?  That would be my best guess at the moment about a likely cause.

---

### Post by N3tMast3r on 2012-07-23
it is just an intel graphic card and i did not install any driver. compiz works fine though... i am thinking about trying to format it and install everything again...

what do you guys think?

---

### Post by sffvba[e0rt on 2012-07-23
> **N3tMast3r said:**
> it is just an intel graphic card and i did not install any driver. compiz works fine though... i am thinking about trying to format it and install everything again...

what do you guys think?

If you end up with exactly the same drivers and software and settings after you re-install you will end up with exactly the same issue...


404

---

### Post by N3tMast3r on 2012-07-23
what do you suggest? :(

---

### Post by Doug S on 2012-07-23
What does top say your total per CPU usage is?
To list each CPU total, instead of the total of all of them, type the "1" (one) key.
Also try the "T" key to observe total time for each process. In your previoous top post you can see some migration processes have used a lot of CPU even though they didn't use any in that sample.
From your top post, my sums come to 74% CPU used (where 200% would be full load on two).
I do not use system-monitor so I don't know if it includes such things as uninterruptable sleep (i.e. waiting for disk i/o), but in top just observe the idle (id) numbers to see if it correlates with (100 -) the system-monitor.

---

### Post by vasa1 on 2012-07-23
> **N3tMast3r said:**
> what do you suggest? :(
If you post any more output from the terminal, place it between code tags: you can click on the # symbol to get a pair of code tags.

---

### Post by vasa1 on 2012-07-23
Why is everything is post #3 running as root?

---

### Post by N3tMast3r on 2012-07-23
> 
Tasks: 138 total,   3 running, 134 sleeping,   0 stopped,   1 zombie
Cpu(s): 39.8%us, 22.7%sy,  0.0%ni, 33.0%id,  4.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3347904k total,   923768k used,  2424136k free,    47656k buffers
Swap:        0k total,        0k used,        0k free,   444128k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 1484 root      19  -1  307m  14m 7764 S   10  0.4   1:03.64 Xorg                                                                                                                
 1649 root      20   0  8516 5164 2220 S   10  0.2   0:12.70 gconfd-2                                                                                                            
 1632 root      20   0  3104 1152  604 S    6  0.0   0:07.68 dbus-daemon                                                                                                         
 6885 root      20   0  384m  91m  20m S    3  2.8   0:08.53 skype                                                                                                               
 1628 root      20   0 25980 6708 5356 S    2  0.2   0:03.49 x-session-manag                                                                                                     
 1671 root      20   0 80688  33m  15m S    2  1.0   0:03.82 compiz                                                                                                              
 7065 root      20   0  487m 196m  32m S    2  6.0   0:21.07 firefox-bin                                                                                                         
 1680 root      20   0 44672  16m  11m S    1  0.5   0:03.44 gnome-panel                                                                                                         
 1690 root      20   0 19760 7356 5908 S    1  0.2   0:01.63 gnome-power-man                                                                                                     
 1957 root      20   0 63140  14m  11m S    1  0.4   0:01.15 clock-applet                                                                                                        
 8657 root      20   0  113m  22m  13m R    1  0.7   0:00.84 plugin-containe                                                                                                     
11580 root      20   0 46904  12m  10m R    1  0.4   0:00.40 gnome-terminal                                                                                                      
 1956 root      20   0 49840  12m 9972 S    1  0.4   0:01.17 indicator-apple                                                                                                     
 2130 root      20   0 24364 4252 3472 S    1  0.1   0:00.75 indicator-appli                                                                                                     
 2231 root      20   0 21208 7760 5892 S    1  0.2   0:00.99 notification-da                                                                                                     
    4 root      20   0     0    0    0 S    0  0.0   0:00.11 kworker/0:0                                                                                                         
   10 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/1                                                                                                         
 1658 root      20   0 89252 9356 7296 S    0  0.3   0:01.49 gnome-settings-                                                                                                     
 1659 root      20   0 23984 1988 1584 S    0  0.1   0:00.62 gnome-keyring-d                                                                                                     
 1663 root      20   0  6424 2236 1904 S    0  0.1   0:00.63 gvfsd                                                                                                               
 1673 root      20   0 85516  15m  11m S    0  0.5   0:01.22 nautilus                                                                                                            
 2092 root      20   0 85132 4496 3608 S    0  0.1   0:00.63 indicator-sound                                                                                                     
 2134 root      20   0 17060 3612 2912 S    0  0.1   0:00.65 indicator-messa                                                                                                     
11912 root      20   0  2592 1120  828 R    0  0.0   0:00.01 top                                                                                                                 
    1 root      20   0  2856 1716 1200 S    0  0.1   0:02.02 init                                                                                                                
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0                                                                                                         
    5 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/u:0                                                                                                         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                         
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                         
    9 root      20   0     0    0    0 S    0  0.0   0:00.57 kworker/1:0                                                                                                         
   11 root      20   0     0    0    0 S    0  0.0   0:00.19 kworker/0:1                                                                                                         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                              
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                                                                                           
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                               
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                         
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                          

I just rebooted but from the system monitor both CPUs are running at about 85%... 

It is running as root because I am using backtrack 5 which is based on ubuntu 10.04...

I do not know what to do :(

---

### Post by sffvba[e0rt on 2012-07-23
> **N3tMast3r said:**
> It is running as root because I am using **backtrack 5** which is based on ubuntu 10.04...

*Thread moved to **Other OS/Distro Talk**.*


404

---

### Post by N3tMast3r on 2012-07-23
The problem was Compiz! Not the cpu usage is back to normal...
I do not understand why Compiz gives me this problem on this laptop... :(

---

