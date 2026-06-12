---
title: "&quot;Error 2&quot; on startup"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by RedViking on 2007-09-16
I just installed Ubuntu on a brand new WD 20gig hard drive.  It installed just fine without any problems, but when I restarted the computer to boot from the disk (instead of LiveCD) the screen says:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 2
_


Then nothing else happens.  What is "Error 2" anyway?  Any suggestions as to how to fix this?  

There is a possibility that the hard drive is faulty (grr...just bought it new).  I earlier tried to install Windows 98 (so I could upgrade to 2000 with my upgrade disk) and the install worked just fine.  But when I tried to boot from the hard drive, nothing would happen.  Same kind of thing.  I wondered if it was related. 

Thanks!

---

### Post by alienexplorers on 2007-09-16
Try reloading grub following the directions in my signature line.

---

### Post by Gerard Barberi on 2007-09-16
You said the hard drive is new?
 
May be some incorrect setting in the BIOS.  Do you have multiple hard drives on your PC?  If so, which is primary, master, etc.?
 
GRUB stage 1 is in the MBR and it looks like you had no problem with that.  Stage 2 requires the menu.lst located on the hard drive.  Perhaps it is having difficulty finiding that file?

---

### Post by RedViking on 2007-09-16
I think I found the problem.  ASDP was disabled in my BIOS.  I enabled it and Ubuntu seems to be working fine now.  Thanks for your help!

---

