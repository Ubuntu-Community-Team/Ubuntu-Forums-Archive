---
title: "Video corruption Live CD Core Duo iMac 20&quot;"
date: 2007-03-03
forum: Apple Intel Users
---

### Post by pschmied on 2007-03-03
Hi, all.  I'm experiencing a problem with Ubuntu Live CDs on my Core Duo 20" iMac.

Video appears normal during the graphical boot sequence (have tested Ubuntu 6.10 and Xubuntu 7.04 Herd 5) up till the point that X starts.  After X starts the video has this odd shearing quality and is unintelligible.  "Start Ubuntu in Safe Graphics Mode" seems to have no effect.

I have installed the latest SMC and EFI firmware from Apple.  I have also installed the latest versions of Boot Camp and rEFIt.

Has anyone seen this before?  Has anyone successfully booted a live CD on a 20" iMac Core Duo system?  Better still, can anyone give me any pointers as to how to fix the problem?

Cheers,
Peter

---

### Post by johnw188 on 2007-03-13
> **pschmied said:**
> Hi, all.  I'm experiencing a problem with Ubuntu Live CDs on my Core Duo 20" iMac.

Video appears normal during the graphical boot sequence (have tested Ubuntu 6.10 and Xubuntu 7.04 Herd 5) up till the point that X starts.  After X starts the video has this odd shearing quality and is unintelligible.  "Start Ubuntu in Safe Graphics Mode" seems to have no effect.

I have installed the latest SMC and EFI firmware from Apple.  I have also installed the latest versions of Boot Camp and rEFIt.

Has anyone seen this before?  Has anyone successfully booted a live CD on a 20" iMac Core Duo system?  Better still, can anyone give me any pointers as to how to fix the problem?

Cheers,
Peter

I've been having the same problem, though I can't for the life of me figure out why

---

### Post by cyberdork33 on 2007-03-13
I get the crazy graphics if I try to go to a virtual console and fixed that by adding a vga=795 to the kernel line Didn't have issues with X though.

---

### Post by macLuntu on 2007-03-19
You have probably solved this by now, but just in case you haven't.
The problem is that the vesa driver, which is loaded by default, doesn't work with the ATI x1600 card in the iMac (17" and 20").

Solution: Boot the liveCd and let it run until everything is nice and distorted. Do ctrl+alt+F1 to get to a new console. Login, and do the following: ```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Get back to the distorted session with ctrl+alt+F7, and then restart X with ctrl+alt+backspace

(You will have to do this again on first boot after installing to the harddrive)

---

### Post by spigolo on 2007-03-19
i had problems with X starting from the live cd, it booted right once every 5 or so (more or less the same with the keyboard). "safe graphics" did it for me though. i wonder how comes if the hardware is the same.

for the kernel line in the grub menu.lst, i find that vga=795 (which corresponds to 1280x) shrinks unevenly the splash on boot up and shut down. i used vga=792 (1024x) better.

---

### Post by cyberdork33 on 2007-03-19
> for the kernel line in the grub menu.lst, i find that vga=795 (which corresponds to 1280x) shrinks unevenly the splash on boot up and shut down. i used vga=792 (1024x) better.

ah, sorry, I do not use the splash, so did not notice.

---

