---
title: "Problems with Ram"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by staar2 on 2007-02-17
I installed first Kubuntu but i didnt like KDE so i installed Gnome to. But now is ram usage up to 700-300 mb. How i can shut some proccess down ?
Little edit to.
Srry didnt explain my problem exactly, my problem is that, it runs to many proccess and takes to much ram, i dont no what proccess need to kill can somone help me with that? I can post here some logs or what ever you want.

---

### Post by Sqwishy on 2007-02-17
Most of the ram ussage is probobly just cache and buffer type stuff, but if you really wana find out what's doing stuff type 'top' in the terminal and it'll show you what's doing what

---

### Post by staar2 on 2007-02-17
Here is my log.
top - 12:29:27 up  2:13,  2 users,  load average: 0.26, 0.13, 0.11
Tasks: 104 total,   1 running, 103 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.9%us,  0.7%sy,  0.0%ni, 80.7%id,  1.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027424k total,   973212k used,    54212k free,    56212k buffers
Swap:  1020116k total,     3788k used,  1016328k free,   567436k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                            
12204 staar2    15   0 64692  19m  14m S 15.3  2.0   0:02.26 gnome-terminal                                     
 4128 root      15   0  386m  58m 8596 S  2.3  5.8   5:10.30 Xorg                                               
10634 staar2    15   0 78144  34m  21m S  0.3  3.5   0:18.29 kopete                                             
12232 root      16   0  2248 1140  844 R  0.3  0.1   0:00.07 top                                                
    1 root      17   0  1632  536  448 S  0.0  0.1   0:01.04 init                                               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0                                          
   10 root      11  -5     0    0    0 S  0.0  0.0   0:13.52 kacpid                                             
   11 root      11  -5     0    0    0 S  0.0  0.0   0:10.31 kacpi_notify                                       
  165 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 kseriod                                            
  198 root      15   0     0    0    0 S  0.0  0.0   0:00.26 pdflush                                            
  199 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush                                            
  200 root      15   0     0    0    0 S  0.0  0.0   0:00.22 kswapd0                                            
  201 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                              
 1772 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                              
 1845 root      10  -5     0    0    0 D  0.0  0.0   0:01.21 kjournald                                          
 1918 root      15   0  1600  548  468 S  0.0  0.1   0:00.01 logd                                               
 2064 root      11  -4  2612 1044  360 S  0.0  0.1   0:00.19 udevd                                              
 2831 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 irda_sir_wq                                        
 2882 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd                                            
 2951 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                          
 3063 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 tifm0                                              
 3092 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pccardd                                            
 3093 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 ipw2200/0                                          
 3164 dhcp      13  -2  2396  564  244 S  0.0  0.1   0:00.00 dhclient3

---

### Post by mcduck on 2007-02-17
RAM that is not used is wasted.

Anyway, 'free -m' gives you easier-to-read info, just read the '+/-buffers & cache'-line.

---

### Post by staar2 on 2007-02-17
total       used       free     shared    buffers     cached
Mem:          1003        986         16          0         51        654
-/+ buffers/cache:        280        722
Swap:          996         13        982

here it is lol free 16mb. How i can make it to take less memory. Are there some memory bugs or what ? How can i turn some services off or programs like in windows service manager and msconfig.

---

### Post by mcduck on 2007-02-17
like I said, read the +/- buffers/cache line.

Your apps are using 280 MB of RAM, with 722MB free memory available at any time.

The rest is used as disk cache, RAM being about 1000 times faster than reading from hard disk. When some app needs more ram cache size is immediately reduced.

---

### Post by louieb on 2007-02-17
> **mcduck said:**
> ...The rest is used as disk cache...
FYI: mcduck got it right. Heres a fuller explanation from the [Gentoo wiki]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management")

---

