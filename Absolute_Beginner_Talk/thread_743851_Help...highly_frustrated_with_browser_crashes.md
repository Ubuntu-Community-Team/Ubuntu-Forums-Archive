---
title: "Help...highly frustrated with browser crashes"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by vol_freak on 2008-04-03
I'm experiencing random crashes of any web browsers I use and even file managers. They just crash and the only error message that shows up is 'segmentation fault (core dumped)'. I've tried every browser I know of and they all crash. It seems to be worse when I'm browsing while doing something resource intensive like backing up or zipping an archive. Any thoughts? It sounds like a hardware issue but I've never experienced any issues on this machine running ubuntu. I've even tried running xubuntu but I get the same issues. 

Where do I start in trying to find out what's happening?

---

### Post by kerry_s on 2008-04-03
sounds like corrupted settings, are you reusing the same /home with each install?

---

### Post by cotcot on 2008-04-03
Have you tried a browser started from a liveCD ? This could tell you if it is a hardware issue.
Maybe check applications running in the back ground. You could switch them of one by one and check if it eliminated the error.

---

### Post by vol_freak on 2008-04-03
> **kerry_s said:**
> sounds like corrupted settings, are you reusing the same /home with each install?Nope. Clean format and install each time. 

> **cotcot said:**
> Have you tried a browser started from a liveCD ? This could tell you if it is a hardware issue.
Maybe check applications running in the back ground. You could switch them of one by one and check if it eliminated the error.

I'm pretty sure it's a hardware/hardware confuration error of some sort. I can duplicate the problem pretty easily by opening a large .tar.gz file and web browsing at the same time. 

I'm going to boot to my ubuntu 7.10 live cd and see if I can duplicate the error from there.

---

### Post by Xiong Chiamiov on 2008-04-03
I don't know that much about seg faults, except that they give me an instant 0 on any project I turn in.  Since I know it's not bad programming, though...

---

### Post by kerry_s on 2008-04-03
what are your specs?
sounds like a memory problem, use the live cd to check the memory.

---

### Post by vol_freak on 2008-04-03
The system is an 2Ghz Athlon XP with 768 mb of ram and a GeForce Fx5500 graphics card.

I ran the ram test from the live CD and assuming it's accurate, it's not a memory issue. The test showed no errors.

I'm thinking maybe a video card issue?? I just don't know what else could be causing it.

---

### Post by philinux on 2008-04-03
Have you got compiz running. If so turn it off see if that helps for now.

---

### Post by vol_freak on 2008-04-03
> **philinux said:**
> Have you got compiz running. If so turn it off see if that helps for now.

Nope. I'm running a very standard install of Xubuntu. 

I just installed the nvidia drivers from the nvidia page but I've still experienced the crashes. I even downloaded the Kazehakase browser to try something different but with the same results. 

So, it doesn't seem to be a ram issue or a video card issue. At this point the only thing that I'm thinking is something with ntfs-3g. When this happens I'm usually copying large files to or from an ntfs drive. I think I'll try commenting out those lines in fstab and see if it happens when copying large files from one linux partition to another. 

Any other suggestions?

---

### Post by vol_freak on 2008-04-03
> **vol_freak said:**
>  At this point the only thing that I'm thinking is something with ntfs-3g. When this happens I'm usually copying large files to or from an ntfs drive. I think I'll try commenting out those lines in fstab and see if it happens when copying large files from one linux partition to another. 

Any other suggestions?

No luck with the above either. I'm out of ideas.

---

### Post by Crafty Kisses on 2008-04-03
> **vol_freak said:**
> No luck with the above either. I'm out of ideas.

Possible RAM issue it sounds like, let's see this, post the following output:
```
top
```

---

### Post by vol_freak on 2008-04-03
> **Codename said:**
> Possible RAM issue it sounds like, let's see this, post the following output:
```
top
```

> top - 23:17:57 up 3 min,  2 users,  load average: 0.26, 0.43, 0.20
Tasks: 108 total,   3 running, 104 sleeping,   0 stopped,   1 zombie
Cpu(s): 80.0%us, 20.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    743028k total,   373956k used,   369072k free,    23096k buffers
Swap:  1646620k total,        0k used,  1646620k free,   213596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 5294 root      16   0  301m  23m 7412 R 57.0  3.2   0:09.41 Xorg                 
 5500 jason     15   0 19296 9960 7116 S 19.0  1.3   0:00.44 xfwm4                
 5556 jason     15   0 76624  19m 9.9m S 19.0  2.6   0:01.14 xfce4-terminal       
 5574 jason     15   0  2364 1152  876 R 19.0  0.2   0:00.17 top                  
    1 root      15   0  2952 1856  532 S  0.0  0.2   0:01.22 init                 
    2 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd             
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0          
    4 root      34  19     0    0    0 R  0.0  0.0   0:00.00 ksoftirqd/0          
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0             
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper              
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0            
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid               
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify         
  119 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod              
  142 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush              
  143 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush              
  144 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0              
  196 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                
 1914 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd        
 1915 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                
 1934 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt             
 1948 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                
 1949 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux              
 2176 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0          
 2516 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kjournald            
 2719 root      18  -4  2996 1348  408 S  0.0  0.2   0:00.57 udevd                
 3105 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 cifsoplockd          
 3106 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 cifsdnotifyd         



This is after I rebooted. I can post after the crashing starts if you would like. I do notice that I'm swapping to harddisk when trying to tar/zip a large 7-9GB file, but I'm sure that's to be expected.

---

### Post by Cato2 on 2008-06-03
I think this is a memory problem, like the others, or perhaps some other hardware problem.  Running memtest86+ would be a good idea - I think Ubuntu has this as an option in most installations (check your /boot/grub/menu.lst has this enabled, then reboot) - or just download the excellent SystemRescueCD and use that, it also includes some hardware tests.

Leave memtest86 running overnight at least to give it a chance to find any problems.  Also maybe see if you can replace the memory.

There is a patch for the Linux kernel called BadMEM that may help - see [http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html](http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html) for background, basically it lets you mark parts of memory as bad and use the rest, which is quite an impressive trick.  Even if you don't use this, the HOWTO has some good background.

---

