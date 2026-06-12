---
title: "System Locking Up"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by pemur1 on 2008-02-26
I posted this question yesterday in a different thread, but never got a response.

The problem I'm having is that my system locks up and the only way I can get it to work is to reboot. The first time it happend was when I was running aMule and listening to music. The second time it happened, I was listening to music and playing Tetravex. I have no idea what to do or how to fix this. Any assistance is greatly appreciated.

---

### Post by Sam Lars on 2008-02-26
Have you tried restarting X, switching terminals, and the SysRq method?
Does it leave anything in dmesg or syslog after it crashes?

---

### Post by pemur1 on 2008-02-26
> **Sam Lars said:**
> Have you tried restarting X, switching terminals, and the SysRq method?
Does it leave anything in dmesg or syslog after it crashes?

Huh?

---

### Post by Sam Lars on 2008-02-26
Sorry for not being more specific. :)
If you press Ctrl+Alt+Backspace, it should restart X and return you to the login screen.
Ctrl+Alt+F1 should take you to a terminal.  From there you can kill a bad application, restart X, etc.
Can you do Alt+Print Screen+B to reboot?
Another freeze problem here.  You can look for more to see if any offer a solution.
[http://ubuntuforums.org/showthread.php?t=693720](http://ubuntuforums.org/showthread.php?t=693720)

---

### Post by Crafty Kisses on 2008-02-26
> **pemur1 said:**
> I posted this question yesterday in a different thread, but never got a response.

The problem I'm having is that my system locks up and the only way I can get it to work is to reboot. The first time it happend was when I was running aMule and listening to music. The second time it happened, I was listening to music and playing Tetravex. I have no idea what to do or how to fix this. Any assistance is greatly appreciated.

Post the following output:
```
top
```

---

### Post by Sam Lars on 2008-02-26
top may work to find something, but not if it's frozen...

---

### Post by pemur1 on 2008-02-26
xxxxxx@xxxxxx-desktop:~$ top

top - 18:28:20 up 3 min,  2 users,  load average: 0.52, 0.58, 0.26
Tasks:  99 total,   4 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.6%us,  0.7%sy,  0.0%ni, 94.7%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    515844k total,   498100k used,    17744k free,    23168k buffers
Swap:  1502036k total,        0k used,  1502036k free,   279024k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4963 root      15   0  325m  43m 6868 R  1.3  8.7   0:11.32 Xorg               
 5473 xxxxxx    15   0 63724  23m  12m S  1.3  4.7   0:04.19 /usr/bin/gnome-    
 5493 xxxxxx    15   0  156m  40m  19m R  0.3  8.0   0:05.55 firefox-bin        
 5510 xxxxxx    15   0 68464  19m  10m S  0.3  3.8   0:00.72 gnome-terminal     
 5530 xxxxxx    15   0  2364 1140  876 R  0.3  0.2   0:00.06 top                
    1 root      15   0  2948 1852  532 S  0.0  0.4   0:01.17 init               
    2 root      12  -5     0    0    0 S  0.0  0.0   0:00.01 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  119 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  142 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush

---

### Post by pemur1 on 2008-02-26
Oh well.

I guess it's back to Xp.

---

