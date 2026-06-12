---
title: "[SOLVED] is it normal when i have win98 installing on virtuabox cpu boost up to 100%"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-31
is it normal when i have win98 installing on virtualbox cpu boost up to 100%. mine is p4 1.8 G
and browsing web page becomes slow also, including this page

---

### Post by skymera on 2007-10-31
well yeah,
your running TWO operatring systems on one 1.8GHz processor,
the windows is very busy installing and that single core is working hard to keep it all running.

seems normal to me

---

### Post by overdrank on 2007-10-31
> **afeasfaerw23231233 said:**
> is it normal when i have win98 installing on virtualbox cpu boost up to 100%. mine is p4 1.8 G
and browsing web page becomes slow also, including this page

Hi and I am using VB on a dual core system and during the installation of windows it did use a lot of the cpu but not when normal use. Also how much ram is dedicated to VB and what is the total amount of the system?

---

### Post by afeasfaerw23231233 on 2007-10-31
>              total       used       free     shared    buffers     cached
Mem:           749        739          9          0         12        267
-/+ buffers/cache:        459        289
Swap:         1466         33       1432

> top - 22:25:42 up  5:56,  3 users,  load average: 2.23, 2.39, 2.18
Tasks: 129 total,   2 running, 126 sleeping,   0 stopped,   1 zombie
Cpu(s): 98.3%us,  0.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:    767388k total,   756884k used,    10504k free,    12596k buffers
Swap:  1502068k total,    34784k used,  1467284k free,   274864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9597 wongs     15   0  155m 115m  12m S 95.7 15.4 291:53.23 VirtualBox         
 4710 root      15   0  234m  32m  12m S  1.7  4.4   3:26.14 Xorg               
 9148 wongs     15   0 98.3m  19m  11m R  1.7  2.6   0:03.15 gnome-terminal     
 9891 wongs     15   0  203m  58m  26m S  0.7  7.8   1:09.74 epiphany-browse    
 2109 root      10  -5     0    0    0 S  0.3  0.0   0:09.56 scsi_eh_1          
 9175 wongs     15   0  2368 1168  876 R  0.3  0.2   0:51.11 top                
 9889 wongs     15   0  168m  48m  22m S  0.3  6.4   1:12.61 firefox-bin        


after reading ''virtualization'' from wikipedia, still not sure what it is. does it mean only cpu from intel and amd which have IVT and AMD-V technology can run virtualbox well? otherwise it would be very slow?
currently i dedicated 64MB ram to virtual98 (coz it's recommanded) but however it is using ~117MB (15.4%)! Why?
i also want to know why there's always 1 inactive program running when i type top

---

### Post by afeasfaerw23231233 on 2007-10-31
bump

---

### Post by ByteJuggler on 2007-10-31
> **afeasfaerw23231233 said:**
> after reading ''virtualization'' from wikipedia, still not sure what it is. does it mean only cpu from intel and amd which have IVT and AMD-V technology can run virtualbox well? otherwise it would be very slow?
currently i dedicated 64MB ram to virtual98 (coz it's recommanded) but however it is using ~117MB (15.4%)! Why?
i also want to know why there's always 1 inactive program running when i type top

Pretty much.  The x86 chips weren't originally made to virtualise, so without IVT/AMD-V running virtual machines must rely on some crude (performance hitting) hacks.  If your CPU is already not one of the fastest to begin with, then this impact can be quite significant. 

As for top: Actually you should see more than just 1 inactive program, most of the time. :-)  Most programs on Linux are in the "S" (Sleeping") state most of the time.

---

### Post by afeasfaerw23231233 on 2007-11-01
i want virtualbox to use fewer of my system resources so that my real box can run faster!
i think i won't buy a new processor since i need to upgrade my mainboard and ram to, and the price of amd-v or ivt cpu is still high (low?) anyone would tell me how to limit the cpu usage of virtualbox?

---

### Post by afeasfaerw23231233 on 2007-11-01
but would a cheapest dual core cpu without amd-v or ivt do the job? (e.g: pentium dual-core, athlon x2 -4000 )
Edit: well, after checking the wikipedia, all athlon x2 socket am2 cpu support amd-v

---

### Post by mandanthe1 on 2007-11-01
I can't speak for anyone else, but VirtualBox likes to go haywire and hog my system resources from time to time.  If that's the case here, then my best solution is to restart your computer.  That did wonders for me the last time VirtualBox acted up on me.

---

### Post by afeasfaerw23231233 on 2007-11-01
virtualbox is sluggish! i have finished installing windows me on it. i am sure the speed is slower than a PI computer does! (though it used up 100% of my cpu) why virtualbox is so sluggish! it uses 15% cpu while my virtual win me is idle , when i have a few click on it, it bursts to 100%, but i have to wait a long time until something shown up. i also want to know why it uses more ram than what it's dedicated (64M):  15.1% x 768 MB = 116MB (almost 2 times )
> 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
22479 wongs     15   0  157m 113m  12m S 96.1 15.1 827:11.43 VirtualBox    

mine P4 1.8G cpu is that bad?

---

### Post by insane_alien on 2007-11-01
it is probably worth mentioning that windows 98 does not use the HLT command. this causes CPU usage to be at 100% ALL the time.

vmware server can force the HLT command  but VB cannot. there are programs out there (one is on [www.majorgeeks.com](www.majorgeeks.com) (something like that anyway)) that you can install to the win98 guest that will make it use the HLT command.

---

### Post by ByteJuggler on 2007-11-01
> **afeasfaerw23231233 said:**
> i want virtualbox to use fewer of my system resources so that my real box can run faster!
i think i won't buy a new processor since i need to upgrade my mainboard and ram to, and the price of amd-v or ivt cpu is still high (low?) anyone would tell me how to limit the cpu usage of virtualbox?

You could consider installing the proprietary (but free to install) VMWare Server which apparently deals a little better with Win98 than Virtualbox.

However, to answer your question, to change the priority of a process you can use the "renice" command from the commandline.  Use "top" or "ps" to find the PID of the running virtualbox process, then use 

```
renice 10 -p 1234
```

Where 10 is the new nice level (the higher the number, the lower priority, up to 19 being the lowest priority, the default being 0, and the highest priority being -19) and 1234 is the PID (replace with the number found from "top".)

This will ensure that Linux will give your other processes priority if they need the CPU, even if virtualbox sucks up all the other CPU cycles that are available. (So, your CPU use will still appear to be 100%, but it shouldn't matter as much because Virtualbox will only get the CPU if no other process needed/wanted it first.)

---

### Post by afeasfaerw23231233 on 2007-11-03
thanks for your help. i may try it

---

### Post by afeasfaerw23231233 on 2007-11-06
i gave up 98 and install 2000 and it runs much better. initially i though 98 would be more suitable than 2000 since it has a lower system requirements. but 2000 now works very well -- 5% cpu at idle and no sluggish at all. thanks for your help. firefox in the virtualbox seems work faster than in my real box!

---

