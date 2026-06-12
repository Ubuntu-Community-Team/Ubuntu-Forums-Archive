---
title: "System gets slow/sluggish/(windows-like) on inactivity"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2006-11-07
hi , ive just installed ubuntu a week ago and im a  lil experienced total newbie. Im having this problem that whenever i keep my system on for about 4 or 5 hours (usually downloading something via BitTornado or even if its like that) it goes very slow and if i try to run any program , it doesnt start up.Please help.
Btw , im using a 2.4 GHz processor with 1 GB DDR RAM and 64 MB Geforce mx 4000 graphic card + 80 GB HD (Seagate).Thanks.

---

### Post by rlozano on 2006-11-07
is it only when you are using bittornado? how about if you just keep it sitting w/o doing anything, does it still slow down?

also, try using Ktorrent, i believe its a better torrent software.

another thing, are you using either beryl or compiz?

let me know your feedback.

---

### Post by ashmew2 on 2006-11-07
Thanks for replying , yeah it happens mostly when i use BitTornado but it also happens when like nothing's on and the system's idle by itself. Plus i dont use either of the software. and there's some new problem on my Ubuntu  , its hanging very frequently now and im using Gnome so Ktorrent will still work or will i have to install KDE. ?

---

### Post by Chayak on 2006-11-07
Thats odd, have you tried having a terminal up and using top when it gets sluggish

---

### Post by ashmew2 on 2006-11-07
when i enter "top" in terminal it gives me :
top - 22:43:28 up  1:07,  2 users,  load average: 2.62, 1.69, 0.96
Tasks:  85 total,   2 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 61.8%us,  6.6%sy,  0.0%ni,  0.0%id, 31.2%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1035728k total,  1021200k used,    14528k free,     1820k buffers
Swap:   522104k total,    17640k used,   504464k free,   804388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7505 ashish    16   0 86128  41m  16m S 54.1  4.1   2:44.67 btdownloadgui      
 3960 root      15   0  347m  48m 7984 S 12.0  4.8   3:38.59 Xorg               
 7705 ashish    15   0 51412  14m 9504 R  1.3  1.4   0:01.03 gnome-terminal     
  127 root      15   0     0    0    0 S  0.3  0.0   0:01.01 kswapd0            
 4415 ashish    15   0 43128  17m  12m S  0.3  1.8   0:16.28 gnome-panel        
 7743 ashish    15   0  2248 1112  840 R  0.3  0.1   0:00.03 top                
    1 root      16   0  1632  540  448 S  0.0  0.1   0:01.04 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   89 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod

---

### Post by David Corrales on 2006-11-07
It's the BtDownloadGUI process as your **top** shows:
PID USER PR NI VIRT RES SHR S **%CPU** %MEM TIME+ COMMAND 
7505 ashish 16 0 86128 41m 16m S **54.1** 4.1 2:44.67 btdownloadgui

---

### Post by ashmew2 on 2006-11-07
so what to do?btw ive disabled the screensaver when sysyem's idle and that had a good effect , system running slow even now but quite faster than before.

---

### Post by polly1 on 2006-11-08
Hi 

Looking at the top info., your memory has nearly all been used up on Bit Torrent, and your swap file has come into play. So there is very little left for any other computer use. This is almost certainly the reason for your machines sluggishness. Suggest you again "top" on terminal, without the use of Bit Torrent and post the results.

---

### Post by ashmew2 on 2006-11-08
top - 20:14:06 up 6 min,  2 users,  load average: 0.01, 0.15, 0.09
Tasks:  84 total,   3 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035728k total,   288284k used,   747444k free,     8748k buffers
Swap:   522104k total,        0k used,   522104k free,   165264k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4710 ashish    15   0  2248 1116  844 R 99.9  0.1   0:00.10 top                
    1 root      16   0  1628  536  448 S  0.0  0.1   0:01.03 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   89 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  125 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  126 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  127 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
  128 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1700 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
top - 20:14:28 up 6 min,  2 users,  load average: 0.14, 0.17, 0.09
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  0.7%sy,  0.0%ni, 93.3%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1035728k total,   288456k used,   747272k free,     8780k buffers
Swap:   522104k total,        0k used,   522104k free,   165300k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND    
The TOP results without BitTOrnado

---

### Post by polly1 on 2006-11-08
Hi 

BitTOrnado is the memory hogger. If you check the 4th line of each top post
you can see the difference in the used and unused memory, I don't think there is much major action you can do to solve the problem.

One thing you can try is to ensure that your kernel is optomised to get the 
best possible performance, by using this command in a terminal.


 [sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686]

You  can also ensure you clear your trash can, and your browsing history on Firefox> Tools<Clear private Data

---

### Post by ashmew2 on 2006-11-08
Thanks for the info , will give it a try asap

---

### Post by ashmew2 on 2006-11-08
k thanks for the info , ill give it a try asap

---

