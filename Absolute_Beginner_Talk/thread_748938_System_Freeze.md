---
title: "System Freeze"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by kevin1780 on 2008-04-07
I finally converted last week after years of contemplation. There are so many things I'm happy about with Ubuntu, I'm going to tough it out with the problems I'm having, most of which I'm sure are part of the learning curve. What I have to figure out soon, though, is why my system is freezing, usually when attempting to download an update or something, but at other times too. I lose mouse and keyboard function, so I can't force quit, and end up having to push the button to power down. Can you help me diagnosis this? I had lots of issues when I was running XP, but never this.

---

### Post by Crafty Kisses on 2008-04-07
First off, can you post your system specs? Also can you post the following output:
```
top
```

---

### Post by spiderbatdad on 2008-04-07
can you upload dmesg like this? [http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)
In post #5.

---

### Post by kevin1780 on 2008-04-08
I have a Dell XPS 200 with 2GB of memory with an Intel Pentium D 820 / 2.80 GHz dual core 64-bit processor. I'm running Ubuntu 8.04 (screen resolution nightmares with previous release that I couldn't resolve trying to reconfigure xorg). 

top - 00:03:27 up 55 min,  2 users,  load average: 0.30, 0.48, 0.65
Tasks: 118 total,   1 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.3%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2053732k total,  1936384k used,   117348k free,   137868k buffers
Swap:  3229024k total,       36k used,  3228988k free,  1166076k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5850 kevin     20   0  501m 115m  23m S    1  5.8   0:57.69 firefox            
 5267 root      20   0  486m  69m 8040 S    1  3.5   6:20.63 Xorg               
 5653 kevin     20   0  121m 5624 3016 S    0  0.3   0:04.90 pulseaudio         
    1 root      20   0  4020  892  604 S    0  0.0   0:02.88 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid   

Would any other info be helpful?  I appreciate you all trying to help. Thanks for your patience with me.

---

### Post by kevin1780 on 2008-04-08
Okay, file successfully attached.  I'll just add that my computer is also running absurdly slow. I just don't get it.

---

### Post by spiderbatdad on 2008-04-08
Did you read  the rest of the previously linked post?
Do you think you can follow those steps...also see the second page for replacing "ro" after reboot.

---

### Post by kevin1780 on 2008-04-08
Okay, I removed the "ro" from all the kernel lines and rebooted.  Do you recommend I also reconfigure xserver-xorg? (This is how I screwed things up before.)  I'm not having any issues with the mouse, keyboard, screen resolution, etc. What would I be aiming to correct by reconfiguring?  Could have editing /boot/grub/menu.lst have fixed this problem by itself? (My computer hasn't shut down yet, but it's only been 5 mintues :D )

Thanks again for all your help.

---

