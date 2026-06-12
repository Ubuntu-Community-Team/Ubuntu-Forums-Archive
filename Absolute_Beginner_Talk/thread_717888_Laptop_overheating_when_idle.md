---
title: "Laptop overheating when idle"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-07
Just switched to Ubuntu 7.10 from windows xp. I'm running:

Acer Asipe 5670
dual intel processor t2300 @ 1.66 ghz each
98.1 GB disk space

On windows, I had a problem with this laptop overheating if I was playing a cpu-heavy game (TF2, etc). Generally the laptop never had a problem with sitting idle however. Now with ubuntu, if I leave my laptop sitting idle for 10+ minutes, the entire surface gets extremely hot. What can I do? And to think I was told ubuntu was easy!

---

### Post by xeth_delta on 2008-03-07
The first thing would be to check whether the CPU is really idle. Open a terminal and run
```
top
```
this will provide you with a list of most active programs.

---

### Post by philosophicscience on 2008-03-07
top - 14:16:46 up  3:20,  2 users,  load average: 0.12, 0.08, 0.08
Tasks: 128 total,   3 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.7%us,  0.5%sy,  0.0%ni, 96.5%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1034112k total,  1017344k used,    16768k free,   202236k buffers
Swap:  3028212k total,    34736k used,  2993476k free,   281732k cached

 5713 micah     15   0  250m  98m  18m S    3  9.7   3:59.87 Xgl                
 5488 root      15   0  201m  28m 8300 S    1  2.8   0:13.11 Xorg               
 8989 micah     15   0 40780  17m  12m S    1  1.7   0:03.72 gnome-system-mo    
 9003 micah     15   0 70196  19m  11m R    1  1.9   0:00.57 gnome-terminal     
 5757 micah     15   0 24580  16m 7524 S    0  1.7   0:08.52 compiz.real        
 6026 micah     18   0  175m  72m  15m S    0  7.2   0:06.88 totem              
    1 root      15   0  2952 1852  532 S    0  0.2   0:01.56 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 R    0  0.0   0:01.53 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

### Post by xeth_delta on 2008-03-07
Is there any noticeable difference in fan bhaviour between your windows and linux installations?
Try installing computertemp and check the temperture. It is in the repositories.

---

