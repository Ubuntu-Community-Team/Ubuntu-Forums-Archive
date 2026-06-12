---
title: "entire desktop/programs running very slowly"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by ministoat on 2007-09-02
i've just made a new install of lastest ubuntu (feisty?) and everything is running extremely slowly compared to the last one - boot time is slow, and opening programs and windows is extremely slow too.

i don't know what info i can add in here to help, but if you tell me i will find it :)

can anyone help with this?

---

### Post by kellemes on 2007-09-02
What hardware you have?
Any compiz or whatever?

---

### Post by justleen on 2007-09-02
have a look at the output of
```
top -n 1 
```
it will list the running proccesses and their cpu load

---

### Post by ministoat on 2007-09-02
i feel pretty dumb because i reinstalled a few drivers and turned the machine off..when i've turned it on this morning everything seems to be working fine!

while having problems i checked system monitor, and found nothing was caning the cpu or ram..setup is

amd64 3700 (2.2ghz)
1gb ram
asus a8v motherboard

---

### Post by ministoat on 2007-09-02
oh and no i didnt have compiz..just set it up tho and the problem seems to be repeating

---

### Post by ministoat on 2007-09-02
here's the running processes from the terminal command:

top - 19:38:15 up 11 min,  2 users,  load average: 0.24, 0.25, 0.15
Tasks:  96 total,   2 running,  93 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.8%us,  1.9%sy,  0.2%ni, 85.4%id,  5.8%wa,  0.2%hi,  0.8%si,  0.0%st
Mem:   1027800k total,   686496k used,   341304k free,    19900k buffers
Swap:  9767512k total,        0k used,  9767512k free,   346228k cached

  PID    USER           PR  NI     VIRT  RES   SHR    S   %CPU %MEM    TIME+    COMMAND            
 4887  haldaemo  18   0 16548   976    820   S      2.0       0.1   0:00.16   hald-addon-stor    
        1 root              18   0    5064 1960   564   S      0.0       0.2   0:00.62    init               
        2 root              RT   0           0        0    0       S      0.0       0.0   0:00.00 migration/0        
        3 root              34  19          0        0    0       S      0.0       0.0   0:00.00 ksoftirqd/0        
        4 root              RT   0           0        0    0       S      0.0       0.0   0:00.00 watchdog/0         
        5 root              10  -5           0        0    0       S      0.0       0.0   0:00.01 events/0           
        6 root              10  -5           0        0    0       S      0.0       0.0   0:00.00 khelper            
        7 root              10  -5           0        0    0       S      0.0       0.0   0:00.00 kthread            
      29 root              10  -5           0        0    0       S      0.0       0.0   0:00.00 kblockd/0          
      30 root              20  -5           0        0    0       S      0.0       0.0   0:00.00 kacpid             
      31 root              20  -5           0        0    0       S      0.0       0.0   0:00.00 kacpi_notify       
    128 root              10  -5          0         0    0       S      0.0       0.0   0:00.00 kseriod            
    158 root              21   0           0        0    0       S      0.0       0.0   0:00.00 pdflush              
    159 root              15   0           0        0     0      S      0.0       0.0   0:00.00 pdflush             
     160 root             16  -5           0        0    0       S       0.0      0.0   0:00.00 kswapd0            
     161 root             16  -5           0        0    0       S       0.0      0.0   0:00.00 aio/0              
   1994 root             10  -5           0        0    0       S       0.0      0.0   0:00.00 ksuspend_usbd

---

### Post by ministoat on 2007-09-02
i spent ages tryin to sort the spacing on that :(

---

### Post by banewman on 2007-09-02
You might need to get hdparm working for you - system-admin-services- scroll down to hdparm and select then reboot. It made a significant improvement on my system. :)

---

### Post by gimpguy2000 on 2007-09-02
Just wanted to say, that was a very helpful tip, hdparm is now going on my system as well and it improved everything 100 fold! :) Runs great, just don't know what hdparm does specifically but whatever, it works great. 


X :)

---

