---
title: "CPU use always at 100%"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-20
I've got a 2.39 Ghz Intel processor. Any system monitor tool is showing my CPU usage to be at 100% at all times. My computer isn't performing slow at all and music isn't lagging or anything like that...

I imagine it can't be to good to always be running at 100%. on WinXP it would only need 7% when idle

---

### Post by Ptero-4 on 2007-03-20
I just ran top and it says 34% CPU use, can you please type ```
top -n 1
``` at the terminal and post the output.

---

### Post by Jormanks on 2007-03-20
I'm having the very same problem.
> 
top - 19:04:55 up 30 min,  2 users,  load average: 1.40, 1.15, 0.78
Tasks: 111 total,   1 running, 109 sleeping,   0 stopped,   1 zombie
Cpu(s): 30.6%us,  3.4%sy,  0.3%ni, 57.6%id,  7.8%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:    970648k total,   957952k used,    12696k free,   219604k buffers
Swap:  2056312k total,    17704k used,  2038608k free,   413108k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4161 root      15   0  233m  35m 8108 S  3.9  3.7   4:28.74 Xorg               
 5692 jormanks  15   0  259m  73m  27m S  3.9  7.8   1:02.82 firefox-bin        
 6188 jormanks  15   0  2244 1056  768 R  1.9  0.1   0:00.02 top                
    1 root      15   0  1628  536  448 S  0.0  0.1   0:01.14 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  105 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush            
  140 root      15   0     0    0    0 S  0.0  0.0   0:00.92 kswapd0      

Thanks

---

### Post by auraithx on 2007-03-20
Ahah! Fixed it, Itunes.exe(Crossover office) and wineserver were running somehow in the background.

I just used a kill -9 and my processor use is between 0-11%~

---

### Post by steve101101 on 2007-03-20
im not sure make sure that it isn't running at the startup by going to system>preferences>sessions. then click on the startup programs tab and make sure an i tunes thing isn't in the list. if it is disable it.

---

### Post by somafm on 2007-03-20
Hello,

I also had this problem. It would happen randomly and I would have to restart, but then it would just come back.

I fixed it by installing Envy as recommended by another thread. Envy will basically detect your video card, install the latest/correct drivers, and configure your xorg.conf file properly.

That seemed to fix the problem considering I have not seen the high cpu usage again and the machine has been up for about a week now :) Good luck! 

*Thought I would add this in case anyone else has this problem and cant figure out a solution*

---

