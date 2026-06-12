---
title: "New install keeps freezing"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Agamon on 2007-01-29
Hi.  I'm a newb here.  I just installed ubuntu 6.10 with no problems.  However, once I'm done logging in, it 's only a matter of time before the desktop graphics begins to 'smear' and the system locks up completely requiring a hard reboot.  What is the problem? Thanks.

---

### Post by taurus on 2007-01-29
Spec of your machine?  Did you install Dapper or Edgy?  Are you running x86 or x86_64?

---

### Post by Agamon on 2007-01-30
I installed Edgy x86_64, dual boot with WinXP.  I'm running an Athlon 64 3800+, 2GB RAM, Geforce 7800 GT, Creative SB X-Fi.

---

### Post by igknighted on 2007-01-30
Sounds like some process crashed in the background or is eating your resources... can you post the results of the command 'top' (without the quotes)?

---

### Post by Agamon on 2007-01-30
How do I save the results to a text file?

---

### Post by igknighted on 2007-01-30
normally 'top > txtfile' would do it, but since top is dynamic it messes that up.  I tried it and it came out all garbled.  Just a simple copy/paste into code tags is fine for posting here.

EDIT: if you really want to use a text file I'd highlight to copy then middle mouse button paste into a text editor (gedit usually)

---

### Post by Agamon on 2007-01-30
I'm posting from a different PC, that's why I need to save it.  I literally have 15 sec to 1 min before it locks up on me.  I'll give that command a shot.

---

### Post by igknighted on 2007-01-30
hmm, yeah, give it a shot... if it will only last for a few seconds before a crash you could try saving to a text file, maybe it wouldnt have enough time to scramble.

---

### Post by Agamon on 2007-01-30
Wow, that was difficult, it kept locking up before I could do anything.  Hope it's useful.

```
top - 22:58:21 up 1 min,  2 users,  load average: 1.07, 0.42, 0.15
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.7%us,  0.0%sy,  0.0%ni, 90.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2573556k total,   304020k used,  2269536k free,    12532k buffers
Swap:  5799392k total,        0k used,  5799392k free,   118164k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4606 keith     15   0  140m  19m  10m S  7.7  0.8   0:02.53 gnome-terminal     
 4084 root      15   0  324m  15m 6964 S  1.7  0.6   0:01.74 Xorg               
 4517 keith     15   0 64132 9584 6980 S  0.7  0.4   0:00.42 metacity           
 4632 keith     15   0  158m  26m  14m S  0.3  1.1   0:00.92 gedit              
    1 root      16   0  2728  596  476 S  0.0  0.0   0:00.62 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    6 root      11  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  144 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  180 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  181 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush  
```

---

### Post by igknighted on 2007-01-30
well, its not a runaway process.  Your CPU is nearly idle, which is good in a way because it eliminates a lot of possiblities.  What type of graphics card do you have?  And have you installed any special drivers for it?

EDIT: Not only is ur CPU not working hard, you are barely using your RAM... likely points to graphics as that has its own CPU and ram

---

### Post by Agamon on 2007-01-30
It's an Nvidia GeForce 7800 GT, and no, I really haven't had a chance to load any drivers.  I could try grabbing some with this PC, pull them through the network and hope it stays up long enough for an install....

Edit: I found 'NVIDIA-Linux-x86_64-1.0-9746-pkg2.run'.  That looks like what I'd need.

---

### Post by igknighted on 2007-01-30
> **Agamon said:**
> It's an Nvidia GeForce 7800 GT, and no, I really haven't had a chance to load any drivers.  I could try grabbing some with this PC, pull them through the network and hope it stays up long enough for an install....

Edit: I found 'NVIDIA-Linux-x86_64-1.0-9746-pkg2.run'.  That looks like what I'd need.

Try this instead... boot into recovery mode, it will take you to the terminal only.  Run the command 'aptitude install nvidia-glx' and then restart normally.  It will install the NVIDIA drivers in .deb form, much easier.  The NVIDIA ones can be quite a pain on Debian/Ubuntu because the run-levels are screwy.

---

### Post by Agamon on 2007-01-30
That didn't seem to help.  Any other suggestions?

---

### Post by igknighted on 2007-01-30
Can you post the xorg.conf file?  Or, when you booted normally after the install did you get an NVIDIA splash screen before the login screen?

---

### Post by Agamon on 2007-01-30
No NVIDIA splash screen.  And considering how tough it was to post 'top', I hope that's good enough. :)

Did the drivers not install, then?

---

### Post by igknighted on 2007-01-30
They installed, the config files needs updating.  Boot again into recovery mode, and once at the prompt open the xorg.conf file:
```
nano /etc/X11/xorg.conf
```

from here, you need to scroll down until you see section that looks roughly like this (but with your hardware):
```
Section "Device"
    Identifier  "VESA"
    Driver      "fglrx" # do not remove vesa
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
EndSection
```

Your driver will say: Driver "nv" and you need to change it to Driver "nvidia"

Thats it.  Save (ctrl+o) and exit (ctrl+x), then reboot and this should do it (assuming the graphics was the issue, which I think is likely).

EDIT: My apologies, I should have had you edit this file earlier, slipped my mind.

---

### Post by Agamon on 2007-01-30
Say, I believe that did it!  Thanks a lot, I really appreciate the help.  If this is a typical example of the community here, then I'm really glad I decided to join in.  Thanks again!

---

### Post by igknighted on 2007-01-30
Thats great to hear... good luck with Ubuntu!

---

