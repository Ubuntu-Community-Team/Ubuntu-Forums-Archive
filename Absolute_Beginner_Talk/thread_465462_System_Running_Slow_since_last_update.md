---
title: "System Running Slow since last update"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by kcw1304 on 2007-06-05
I have a Dell Ispiron 600m, pentium III, 500MB memory, 60GB hard drive running fiesty. The system monitor says I'm using 85% (425MB) of my memory but the 'processes' tab doesn't show that much memory being used for listed processes.
I saw on a different post to run top- here is the output from that while running firefox, thunderbird, text editor, oowrite and R (stats program):

top - 15:38:25 up  3:50,  3 users,  load average: 1.27, 1.66, 1.85
Tasks: 107 total,   1 running, 104 sleeping,   1 stopped,   1 zombie
Cpu(s):  7.7%us,  1.0%sy,  0.0%ni, 26.3%id, 64.3%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    515888k total,   509880k used,     6008k free,      268k buffers
Swap:        0k total,        0k used,        0k free,    58828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7402 kelly     15   0  230m  61m 6008 S  4.0 12.1   8:20.06 firefox-bin        
 5008 root      15   0  310m 216m 2072 S  3.0 42.9   8:14.48 Xorg               
12595 kelly     15   0  2320  744  464 R  0.7  0.1   0:00.18 top                
 8156 kelly     15   0  3984 1308  300 S  0.3  0.3   0:11.07 wineserver         
12024 kelly     15   0 59236 9564 3600 S  0.3  1.9   0:02.41 gnome-terminal     
12181 kelly     17   0  115m  22m 4016 S  0.3  4.5   0:13.40 mozilla-thunder    
    1 root      15   0  2912 1496  172 S  0.0  0.3   0:01.57 init               
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.12 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    6 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   29 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kblockd/0          
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   31 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  139 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  158 root      15   0     0    0    0 S  0.0  0.0   0:00.08 pdflush            
  159 root      15   0     0    0    0 S  0.0  0.0   0:00.06 pdflush       

Any ideas??

---

### Post by Pragmatist on 2007-06-05
Please post the output to this command:
```
free -mt
```

---

