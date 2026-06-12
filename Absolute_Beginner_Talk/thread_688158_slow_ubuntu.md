---
title: "slow ubuntu"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by fahadrather on 2008-02-05
whenever i view videos on youtube, my system slows down. first i thought that it was due to the desktop effects because i heard that my card (nvidia geforce 8400gs) is having some issues with ubuntu. so i set my effects to none...still nothing happened...and it is the browser which causes me more problems...it takes a hell lot of time to switch between tabs..:mad:.....help

---

### Post by jan quark on 2008-02-05
what browser do you use? firefox?

did you encounter this slow internet behavior also in other browser?

perhaps disabling ipv6 in the about:config of firefox will bring some help

---

### Post by fahadrather on 2008-02-05
> **jan quark said:**
> what browser do you use? firefox?

did you encounter this slow internet behavior also in other browser?

perhaps disabling ipv6 in the about:config of firefox will bring some help

i dont have problems with internet...it the system..and the browser...i use only firefox..and the ipv6 is turned off..

---

### Post by spiderbatdad on 2008-02-05
also: many of us edit /etc/modprobe.d/aliases to look like the screenshot below.

---

### Post by fahadrather on 2008-02-05
> **spiderbatdad said:**
> also: many of us edit /etc/modprobe.d/aliases to look like the screenshot below.

i have done that as well..while searching for, how to make internet conn. quicker...

---

### Post by spiderbatdad on 2008-02-05
have you tried the top command to see what might be using your resources?```
top
```

---

### Post by fahadrather on 2008-02-05
top - 00:10:27 up 49 min,  3 users,  load average: 0.63, 0.84, 0.81
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.5%us,  1.8%sy,  0.0%ni, 79.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2074792k total,  1164152k used,   910640k free,   162828k buffers
Swap:  2046968k total,        0k used,  2046968k free,   564172k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7512 fahad     15   0  223m  84m  26m S   24  4.2   3:59.96 firefox-bin       
 7186 root      16   0 87708  52m 9124 S   12  2.6   7:54.69 Xorg               
 7363 fahad     15   0 58836  29m 9180 S    4  1.4   1:56.18 compiz.real        
 2200 root      10  -5     0    0    0 S    0  0.0   0:00.26 ata/1              
 8520 fahad     15   0  2368 1180  876 R    0  0.1   0:00.07 top                
    1 root      18   0  2952 1852  532 S    0  0.1   0:01.55 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.13 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.09 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.07 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      18  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0          



it kept changing...hehe...now what??

---

### Post by depeo on 2008-02-06
I have the same graphics card(8400GS) I recommend you to get another, my Ubuntu is snappier on a ATI-card with VESA-mode than that card with appropriate drivers. :(

I never realized how fast Ubuntu could be. :)

---

### Post by erginemr on 2008-02-06
If the slowdown occurs only when you are playing youtube videos, a buggy adobe flash driver might be the culprit. You may consider uninstalling "flashplugin-nonfree" form Synaptic and download and install the newest plugin for Linux from Adobe web site.

---

### Post by fahadrather on 2008-02-08
> **erginemr said:**
> If the slowdown occurs only when you are playing youtube videos, a buggy adobe flash driver might be the culprit. You may consider uninstalling "flashplugin-nonfree" form Synaptic and download and install the newest plugin for Linux from Adobe web site.

i had earlier uninstalled that plugin and downloaded and installed the latest tar.gz file from adobe website..........

---

