---
title: "Memory problems in Gutsy?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-12-24
I just un-installed VMware server and noticed that of my 512mb of RAM on my laptop, system monitor lists that more than 50% is used up right after loading ubuntu.... this can't be right?? Any suggestions for fixing this?

---

### Post by ~LoKe on 2007-12-24
When you type "**top**" into the terminal, does it list anything using a large amount of resources?

---

### Post by tonycm1 on 2007-12-24
Xorg and firefox are the top 2 memory users at roughly 10% each.... but with 512mb of ram on my laptop, it still doesn't account for 50-60% memory usage :S

would vmware server have "stolen" ram and made it unusable even after i've uninstalled it??

---

### Post by p_quarles on 2007-12-24
What's the output of
```
free
```
I ask just because it's hard to tell from your first post whether the amount of RAM being used includes the cache and buffer.

---

### Post by ~LoKe on 2007-12-24
> **tonycm1 said:**
> Xorg and firefox are the top 2 memory users at roughly 10% each.... but with 512mb of ram on my laptop, it still doesn't account for 50-60% memory usage :S

would vmware server have "stolen" ram and made it unusable even after i've uninstalled it??

Load up synaptic (**gksu synaptic**) and search for VMWare to see if there are any packages you forgot to install.

---

### Post by ~LoKe on 2007-12-24
> **p_quarles said:**
> What's the output of
```
free
```
I ask just because it's hard to tell from your first post whether the amount of RAM being used includes the cache and buffer.

Cache shouldn't fill up so quickly immediately after booting, and if it does there's another problem to look into. =P

---

### Post by tonycm1 on 2007-12-24
This is what "free" generates:

> tony@tony-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        507596     486184      21412          0       6148     156268
-/+ buffers/cache:     323768     183828
Swap:      1485972      32596    1453376


and "top" generates:

> tony@tony-laptop:~$ top

top - 14:24:44 up 30 min,  2 users,  load average: 0.04, 0.13, 0.29
Tasks: 106 total,   1 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.3%us,  1.0%sy,  0.0%ni, 93.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    507596k total,   488092k used,    19504k free,     6284k buffers
Swap:  1485972k total,    32596k used,  1453376k free,   156676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
 5039 root      15   0  403m  55m 7644 S  3.3 11.2   2:07.69 Xorg                
 5596 tony      16   0 49176  19m  14m S  2.0  3.9   0:37.18 gnome-system-mo     
 5410 tony      15   0 20272  13m 6736 S  0.3  2.8   0:04.74 compiz.real         
 5660 tony      15   0  167m  52m  21m S  0.3 10.5   0:31.45 firefox-bin         
 5692 tony      15   0 90012  21m  12m S  0.3  4.4   0:00.73 gnome-terminal      
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:01.43 init                
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd            
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0         
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.19 ksoftirqd/0         
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0          
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper             
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0           
   27 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid              
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify        
  148 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod             
  167 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush             
  168 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush             
  169 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kswapd0             
  220 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0               
 2011 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd       
 2012 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd               
 2114 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 ata/0               
 2115 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux             
 2206 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 scsi_eh_0           
tony@tony-laptop:~$ 


System monitor states that i'm using 64% of my User Memory (512mb) only have Firefox (2 tabs), terminal, and system monitor.... that can't be right :S

---

### Post by tonycm1 on 2007-12-24
Did a search in Synaptic and found that "Xorg" that is running on my system is part of vmware... i'm going to uninstall it right now. Hopefully that solves it....

---

### Post by ~LoKe on 2007-12-24
> **tonycm1 said:**
> Did a search in Synaptic and found that "Xorg" that is running on my system is part of vmware... i'm going to uninstall it right now. Hopefully that solves it....

xserver-xorg?  Er...please don't uninstall that. ;)

---

### Post by p_quarles on 2007-12-24
> **~LoKe said:**
> xserver-xorg?  Er...please don't uninstall that. ;)
+1. You won't like what happens if you remove that. 

You can find out what specific processes are running by typing this:
```
ps aux
```
If anything VMware related shows up *there*, that might be the problem.

---

### Post by tonycm1 on 2007-12-24
Uninstalled Xorg, rebooted, and user memory still at 50% immediately after reboot :S

Any ideas?

---

### Post by ~LoKe on 2007-12-24
> **tonycm1 said:**
> Uninstalled Xorg, rebooted, and user memory still at 50% immediately after reboot :S

Any ideas?

Pretty sure you didn't uninstall xorg, but that's a good thing.  Yes, try
```
ps aux
```
or
```
ps aux|grep ware
```

---

### Post by tonycm1 on 2007-12-24
I should have clarified.... it was:
X.Org X server -- VMware display driver 

that i uninstalled, not my Voodoo display driver :P

---

### Post by tonycm1 on 2007-12-24
> tony@tony-laptop:~$ px aux|grep ware
bash: px: command not found
tony@tony-laptop:~$ ps aux|grep ware
tony      5822  0.0  0.1   2976   752 pts/0    R+   14:40   0:00 grep ware
tony@tony-laptop:~$ 


Only using 0.1% memory :S

why on earth is system monitor displaying over 50% with nothing open :S

Right now for example, I have firefox (2 tabs), system monitor, terminal, and gedit open.... this is apprently consuming 75% of my user memory 363 of 495mb.... doesn't make any sense

---

### Post by p_quarles on 2007-12-24
> **tonycm1 said:**
> Only using 0.1% memory :S

why on earth is system monitor displaying over 50% with nothing open :S

Right now for example, I have firefox (2 tabs), system monitor, terminal, and gedit open.... this is apprently consuming 75% of my user memory 363 of 495mb.... doesn't make any sense
It's just how Linux does memory management. My guess is that this is no different from how it was in the past, you just may not have noticed.
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by ~LoKe on 2007-12-24
> **tonycm1 said:**
> Only using 0.1% memory :S

VMWare isn't listed.  That 0.1% is from the grep command I believe.

The problem resides elsewhere...I'll try to do some research.

---

### Post by ~LoKe on 2007-12-24
> **tonycm1 said:**
> Right now for example, I have firefox (2 tabs), system monitor, terminal, and gedit open.... this is apprently consuming 75% of my user memory 363 of 495mb.... doesn't make any sense

It's doing its job if you're using up most of your ram.  It's caching information to make applications/etc load faster the next time.  This is good.  The only time you need to worry is if it's hitting your swap space for no reason.

---

### Post by mivo on 2007-12-24
Read here about how Linux manages memory (this is different from how Windows does it): [Linux Memory Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management"). This may explain why most of the memory "seems" to be in use. :)

---

### Post by tonycm1 on 2007-12-24
Thanks a lot guys :) i'm going to read up on Linux memory management a llittle.... i think the problem here might rest between my chair and keyboard (ie. me)... lol

Thanks again :)

---

