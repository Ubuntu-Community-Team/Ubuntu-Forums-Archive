---
title: "Installer stops at detecting network hardware"
date: 2005-06-16
forum: Apple PPC Users
---

### Post by zxee on 2005-06-16
I'm trying to install Hoary to a beige G3. Using bootx with the parameters I found here I was able to get the install started but it gets to a dialogue box "Detecting network hardware" a message on the screen says "Detecting hardware please wait..." after a few minutes the cd stops spinning, the progress bar stays at zero and it stays that way indefinately. 
This G3 is a 300Mhz not much ram 96MB ( I should add more I know )
external modem ethernet two hard drives (IDE)
I have Ubuntu installed on a homebuilt athlon. I'd like to get it running on this PPC if possible. Any hints? Thanks

(Added 6-17-05) Maybe I didn't title this well, or something. I kept working on this problem and re-reading the ubuntu old world mac install how-to, and found I got more frustrated. I sort of expect that now on a mac  :-x . The how-to is not very readable, and AFAI can tell the links are all dead. I went directly to the debian site and some of their links don't work. Perhaps that has something to do with the age of these old world macs?

So I dug around and found an linuxppc (2000) cd. It actually installs from the cd-no bootx, disk floppies or going into OF needed! 
So why five years later is ubuntu unable to create an installer for this machine?
The code obviously is there since linuxppc did it, and I guess it has to be GPL.

I really like ubuntu (on my athlon) but I am disappointed in the lack of ppc support.
I guess I can use the linuxppc install and upgrade the kernel or go with FC4.

---

### Post by jonatin on 2005-06-18
The ubuntu CD may not have the required kernel modules.  I've had that problem with other PowerPC distros not detecting hardware.  the Ubuntu CD won't even boot on my Blue&White G3 without me waving chickenbones over it.  I'd say the age of the machine is part of that issue, I doubt that older hardware is compiled in the default kernel.

Have you tried the LiveCD?  If that works, or if you wish to install linuxppc, perhaps you could run lspci and lsmod and determine the configuration of the hardware?

Unfortunately, in any case, you will likely need to compile a custom kernel for the machine once you've determined the necessary kernel modules.

---

### Post by zxee on 2005-06-20
[QUOTE=jonatin]The ubuntu CD may not have the required kernel modules.  I've had that problem with other PowerPC distros not detecting hardware.  the Ubuntu CD won't even boot on my Blue&White G3 without me waving chickenbones over it.  I'd say the age of the machine is part of that issue, I doubt that older hardware is compiled in the default kernel.

Have you tried the LiveCD?  If that works, or if you wish to install linuxppc, perhaps you could run lspci and lsmod and determine the configuration of the hardware?

Unfortunately, in any case, you will likely need to compile a custom kernel for the machine once you've determined the necessary kernel modules.[/QUOTE]

Thanks for the reply. I did a successful install of linuxppc 2000 of course the issues I experianced with that distro years ago ( won't recognize external GV modem) make it a less than practical install. My point was that since linuxppc installs from the cd why can't developers of ubuntu refer to that code? In fairness I guess there are not a lot of these machines out there plus also wanting to run linux.
BTW I did try the ubuntu live cd-it doesn't work. I was able to finally get both debian boot floppies created ( it was so long ago when I first did that that I had forgotten how to do it) So I may try to install the latest stable debian-sarge 3.1.

---

