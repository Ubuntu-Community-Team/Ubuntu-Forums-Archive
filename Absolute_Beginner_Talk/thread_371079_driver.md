---
title: "driver"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by tagu on 2007-02-26
I have installed Ati binary .xorg driver. Is it enough for display driver? By the way, When I sad I have installed, I installed it from applications->add-remove programs thats all. I want to install beryl also and if I install it now does my system crash?

Thanks...

---

### Post by Maestro23 on 2007-02-26
What do the following commands produce:

From a terminal:

> fglrxinfo

and

> glxinfo | grep direct

---

### Post by tagu on 2007-02-26
tagu@tagu-host:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

tagu@tagu-host:~$ glxinfo | grep direct
direct rendering: No
tagu@tagu-host:~$ 

I think it didn't work, how do I install my driver Any idea? I use ati radeon 9600 can u help me please??

---

### Post by Maestro23 on 2007-02-26
Yeah, no driver installed.  

1. Download the correct driver for your card.

2. Run the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works for both ATI and Nvidia.

Good luck.

---

### Post by igknighted on 2007-02-26
Uninstall your driver from apt first!  Otherwise running the Envy script could cause issues.

---

### Post by tagu on 2007-02-26
you mean .Xorg thing??

---

### Post by 67GTA on 2007-02-26
Envy worked perfectly for me about 5 minutes ago after trying to get the driver and direct rendering working for about a month](*,) .

---

### Post by igknighted on 2007-02-26
You probably installed a package called xorg-driver-fglrx via add/remove.  You need to uninstall it before you install a different version of the drivers or they might conflict.  Try "sudo apt-get remove xorg-driver-fglrx" in the terminal, should take care of it.

---

### Post by Maestro23 on 2007-02-26
> **igknighted said:**
> You probably installed a package called xorg-driver-fglrx via add/remove.  You need to uninstall it before you install a different version of the drivers or they might conflict.  Try "sudo apt-get remove xorg-driver-fglrx" in the terminal, should take care of it.

Thanks IG, I left out that step for him.  Could have been bad ju-ju indeed.:)

---

### Post by tagu on 2007-02-26
Thanks lot I'm doing it now, I will be back after doing what u say :D

---

### Post by tagu on 2007-02-27
First of all, I installed my ati driver and I'm saying that If anyone need ati driver installation,  [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) web site works.

Secondly, I installed beryl with no problem but When I open beryl-manager I can't configure it I think. I made changes but It does not work, I use the commands to rotate screen or rain effect (these are examples) beryl does not work?

Why does not beryl works? Any idea, help? 

Im waiting for your response ;)

---

