---
title: "Can't Boot Ubuntu after install"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by dibbz on 2007-04-15
OK so I went through the Ubuntu setup via the Live CD, created partitions on my second hard drive (one for root and one for swap). Now when it asked where to install GRUB it, by default, gave me hd0, which I don't recognise. My partitions were something like hda. 

Anyways the install went fine, it then asked me to restart or continue on the Live CD. I tried to restart and it ejected the disk and told me to press enter. When I closed the tray and pressed enter nothing happened. It just froze on me. So I had to do a hard reboot. 

When I turned my computer back on it automatically boots into my primary hard drive, Windows XP. 

I assumed that GRUB installed and it would have poped up allowing me to choose what to boot. Now I'm stuck and have no where to go. Does anyone know whats going on here?

---

### Post by reality_hunter on 2007-04-15
in the bios you can change your boot priority.  Change it, so that it boots from the slave not from the master....try it
post the outcome back here.............hope this works

---

### Post by Seisen on 2007-04-15
What you did was install Grub on your slave drive instead of the master drive.

---

### Post by dibbz on 2007-04-15
Posting this from Ubuntu. 

Thanks guys, I changed priority of my drives and GRUB showed up. Haven't tried a restart with Ubuntu yet though, but hopefully it will be ok.

---

### Post by reality_hunter on 2007-04-15
your welcome...
also it won't be a problem after you restart....it will be good from now on.  have fun learning and playing with your UBUNTU

---

