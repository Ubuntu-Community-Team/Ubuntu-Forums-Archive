---
title: "Temporary system freezes?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by DanielJackins on 2008-02-15
Every once in a while (this actually just started happening tonight) my whole screen freezes up for about 20 seconds. Everything is fine after that, but at the time it was happening my processor was 100% in use.

Anybody know why this is happening?

---

### Post by ashmew2 on 2008-02-15
Run "top" in terminal and post the output. As well as , are you using Wine/Cedega for running any Windows Apps ?

---

### Post by Dekunuts on 2008-02-15
Did you install anything new or change some config? I'm asking because I've been having the same problem for weeks (mouse moves but nothing responds for 10-20 seconds) and there are a lot of others with this problem as well. Your information could be useful.

---

### Post by DanielJackins on 2008-02-15
top - 08:17:51 up 1 day, 16:29,  2 users,  load average: 0.11, 0.06, 0.02
Tasks: 108 total,   2 running, 104 sleeping,   0 stopped,   2 zombie
Cpu(s):  0.3%us,  0.3%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2465028k total,  2272584k used,   192444k free,   190256k buffers
Swap:  4803392k total,        0k used,  4803392k free,  1678692k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
18174 root      15   0  129m  69m 8832 R  0.7  2.9  13:39.26 Xorg               
26293 daniel    15   0  2364 1148  876 R  0.3  0.0   0:00.01 top                
    1 root      18   0  2952 1856  532 S  0.0  0.1   0:01.10 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   2:24.66 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.54 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  161 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  185 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush            
  187 root      15  -5     0    0    0 S  0.0  0.0   0:00.05 kswapd0            
  238 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 2014 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 ksuspend_usbd 



Yes I did recently update actually, and I remember when I did that I got an error for one of the installations of an update, though I'm not sure which one

---

### Post by justleen on 2008-02-15
Try to post the output of top when its freezing.. the post above is 99% idle... :)

---

