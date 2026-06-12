---
title: "Getting Error After Disc Loads to First Menu"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Adabard on 2007-03-18
I am trying to install Ubuntu 6.10 on my old laptop, it has a Pentium II processor and 128 mb of RAM. It is an IBM Thinkpad 600E. That's pretty much it...
It will load to the first screen where it gives the menu, but when I choose to "Start or Install from CD" the screen goes black and then displays the following error message:

[     48.251174 ] invalid compressed format (err=2)
[     48.257402 ] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(1,0)
[     48.257485 ]

---

### Post by chuckyp on 2007-03-18
Reboot the system and on the first menu that pops up booting from the CD select Check Disk for Errors.

---

### Post by Adabard on 2007-03-18
I've already done that and it passed all the checksum errors.

---

### Post by Adabard on 2007-03-18
Also, I tested the CD on another computer and it booted to the Live CD version and was ready to install, but that's not the computer I want Ubuntu on... :(

---

### Post by oilchangeguy on 2007-03-18
your computer does not meet the requirements to run ubuntu 6.10. you might try xubuntu 6.10. or damn small linux.

---

### Post by lizardbrain on 2007-03-20
Same error message I'm getting.

This cd has run and installed Ubuntu 6.10 on two other computers. The computer I'm trying it in now is an IBM Thinkpad 600X.

The Thinkpad is currently running Mandriva. My Gentoo live cd boots and runs just fine in it. Ubuntu live cd doesn't. What about the system would run a resource hog like Mandriva and not Ubuntu?

---

### Post by azero on 2007-03-22
Upgrade your laptop's bios. Had the same problem. Downloaded spsdib54.exe, BIOS - System Program Service Diskette from IBM support page: [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=DSHY-3VRJPK](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=DSHY-3VRJPK)
and updated BIOS from floppy. 
Second problem Ubuntu boots from cd, shows gui (X windows?) and hangs at some loading point...

---

### Post by azero on 2007-03-23
Ok, problems solved for me:)

Download ubuntu-6.10-alternate-i386.iso instead of ubuntu-6.10-desktop-i386.iso
It is alternate install and has text-based install. So ubuntu wont boot in your ram before installation, won't take all ram and die :)

P.S. I'm going to use icewm desktop manager, cause for TP600 300Mhz with 128MB ram gnome is to "heavy"

P.P.S. for TP600 tips, read [here ]("http://ubuntuforums.org/showthread.php?t=188736") and [here]("http://www.mueller.ch.vu/misc/tp600e_en.html") do not copy/paste blindly, because second link is for TP600E.

---

