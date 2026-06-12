---
title: "Is my laptop dying?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by eamonn on 2007-09-15
So, I had to reinstall ubuntu today and I got everything running the way it was before I had to do a reinstall. 

A brief note about why I had to reinstall. The 3D cube effect in compiz, and that film strip effect (the one that happens when you hit CRTL+ALT+DOWN), stopped working. I tried fixing it and failed miserably so I had to reinstall.

Anyway, so I get the computer up and running again today. Reinstall ubuntu, my themes, icons, and everything else I had on it before. After a few hours the cube and the film strip effect stop working. 

The other problem that has popped up is that, twice now, I've had my screen lockup on me, try to manually restart the computer, and just have it go black. As if I never tried to restart it, as if I didn't hit the power button to turn it back on after it had been off for a while, as if it was just off and not coming back on for a while. 

I have back and running but I don't trust that it's going to last that long. I've been having problems overheating lately, because bad insulation in my apartment keeps it thirty degrees hotter inside, and I'm beginning to suspect that my hardware may have suffered permanent damage. Furthermore, I went through the System Log and found the following entry in the Xorg.o.log section:

> Broken BIOSes cause the system to hang here. If you encounter this problem please add Option "DisplayInfo" "FALSE" to the Device section of your XF86Config file

The other error I notice a lot was:

> Sep 15 18:16:22 eamonn-laptop kernel: [    8.025731] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')

Sep 15 18:16:22 eamonn-laptop kernel: [    8.025734] Please report the result to linux-kernel to fix this permanently

So, what's going on? Is my laptop dying or can I fix this?

---

### Post by st33med on 2007-09-15
Yes. I am hacking into it currently and pwning ur 3y373m. ;)

Joking aside, you might want to send it to your manufacturer to see if anything has gone awry.

---

### Post by Niklas Schröder on 2007-09-15
which verstion of compiz are you using?  the basic one that comes with ubuntu feisty?  or fusion?

---

