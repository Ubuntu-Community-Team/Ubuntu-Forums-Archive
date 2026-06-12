---
title: "[SOLVED] System running slowly"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by fatherdaly on 2008-02-19
Just recently ubuntu has been running really slow, and I can't figure out why.

I can log on, and If I just use the file browser, everything is fine. But as soon as I start an application, everything slows down. 

I looked at the system monitor, and trackerd seems to be eating quite a bit of memory. I read that it was just a search indexer, so why is it on constantly? Also, when I tried to kill it, it won't let me...

here's a screenshot of system monitor:

[IMG]http://img215.imageshack.us/img215/8926/shotwv2.png[/IMG]

:confused:

---

### Post by SunnyRabbiera on 2008-02-19
well I know that there is/ was an issue with the kernel update chewing up memory...
did you recently update your system?

---

### Post by fatherdaly on 2008-02-19
yea, how can I tell if this is the problem?

btw sorry for the huge image

---

### Post by philinux on 2008-02-19
I've found system monitor sometimes gets the info wrong. Open a terminal and use the

top

command to see what's eating resources.

---

### Post by SunnyRabbiera on 2008-02-19
> **fatherdaly said:**
> yea, how can I tell if this is the problem?

btw sorry for the huge image

If your computer is sluggish, you will know.
But there seems to be another update, at least in my case where the slowdown issue is non existent... but then again I use mint so go figure.

---

### Post by fatherdaly on 2008-02-19
I did the top command:

```
top - 16:46:05 up 31 min,  2 users,  load average: 5.60, 4.50, 2.89
Tasks: 123 total,   1 running, 121 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.9%us,  1.9%sy,  0.0%ni, 46.1%id, 48.0%wa,  0.4%hi,  0.8%si,  0.0%st
Mem:    514252k total,   508336k used,     5916k free,     2504k buffers
Swap:  1502036k total,   687800k used,   814236k free,    44296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6079 fatherda  15   0 33724 7424 4516 S    4  1.4   1:22.60 gnome-system-mo    
 5741 fatherda  15   0  235m  30m 6672 S    3  6.1   1:24.25 Xgl                
 5799 fatherda  34  19  504m 261m 1000 S    2 52.0   2:36.82 trackerd           
 6053 fatherda  15   0  229m  52m  18m S    1 10.5   1:23.68 firefox-bin        
 3898 root      13  -2  1764  256  176 S    0  0.0   0:01.17 ipw3945d-2.6.22    
    1 root      18   0  2968  276  272 S    0  0.1   0:01.48 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.03 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.25 kblockd/0          
Help for Interactive Commands - procps version 3.2.7
Window 1:Def: Cumulative mode Off.  System: Delay 3.0 secs; Secure mode Off.

  Z,B       Global: 'Z' change color mappings; 'B' disable/enable bold
  l,t,m     Toggle Summaries: 'l' load avg; 't' task/cpu stats; 'm' mem info
  1,I       Toggle SMP view: '1' single/separate states; 'I' Irix/Solaris mode

  f,o     . Fields/Columns: 'f' add or remove; 'o' change display order
  F or O  . Select sort field
  <,>     . Move sort field: '<' next col left; '>' next col right
  R,H     . Toggle: 'R' normal/reverse sort; 'H' show threads
  c,i,S   . Toggle: 'c' cmd name/line; 'i' idle tasks; 'S' cumulative time
  x,y     . Toggle highlights: 'x' sort field; 'y' running tasks
  z,b     . Toggle: 'z' color/mono; 'b' bold/reverse (only if 'x' or 'y')
  u       . Show specific user only
  n or #  . Set maximum tasks displayed

  k,r       Manipulate tasks: 'k' kill; 'r' renice
  d or s    Set update interval
  W         Write configuration file
  q         Quit
          ( commands shown with '.' require a visible task display window ) 
Press 'h' or '?' for help with Windows,
any other key to continue 

```

It seems to be roughly the same, as the system monitor

---

### Post by fatherdaly on 2008-02-19
Please, does anyone have any ideas?

This is really annoying me. It only slows down once I've opened an application, and its not just because I've got a slow computer - its been fine until just recently.

:?

Also, the problem still happens in Gnome failsafe mode


Another Edit: I just figured out how to disable the indexing, never mind. Thanks for the help

---

