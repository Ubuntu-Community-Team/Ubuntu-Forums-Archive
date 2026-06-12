---
title: "Ubuntu 6.10 Server CD Won't Boot"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by byronfromwesleyan on 2007-02-12
Hi there.  I'm trying to install Ubuntu Server 6.10 on an older Compaq Proliant 1850R.  I've upgraded the BIOS as far as I can go, but I cannot get the Ubuntu CD to boot.  I've burned ISO images before, so that's not the problem.  I know the box will boot from a CD because I have a Win2k3 CD, also from an ISO, that that boots up just fine.  I even tried Smart Boot Mgr, to no avail.  I can even boot the Windows CD from there, but the Ubuntu CD does nothing.  I've tried 4 different burned CDs, to no avail.  Anyone have any ideas?  Thanks!

---

### Post by rccharles on 2007-02-12
> **byronfromwesleyan said:**
> Hi there.  I'm trying to install Ubuntu Server 6.10 on an older Compaq Proliant 1850R.  I've upgraded the BIOS as far as I can go, but I cannot get the Ubuntu CD to boot.  I've burned ISO images before, so that's not the problem.  I know the box will boot from a CD because I have a Win2k3 CD, also from an ISO, that that boots up just fine.  I even tried Smart Boot Mgr, to no avail.  I can even boot the Windows CD from there, but the Ubuntu CD does nothing.  I've tried 4 different burned CDs, to no avail.  Anyone have any ideas?  Thanks!

I remember some way old computers could not read cd-rw cds but could read cd-r cds.  I'd try booting the cds in some other machine or at least reading them.

You could take your harddrive out of the PC and install it ins some other machine and install Ubuntu then move the drive back to your PC. After moving the harddrive back, do:

make a backup copy of your /etc/X11/xorg.conf file and try:

sudo dpkg-reconfigure xserver-xorg

to recreate xorg.conf file.

Robert
Edit/Delete Message


Robert

---

### Post by rccharles on 2007-02-12
Try putting in some other cd-rom drive.

Robert

---

### Post by byronfromwesleyan on 2007-02-13
Thanks to everyone who replied, but I solved the issue myself (sorta').  I downloaded/burned version 6.06; that version booted with no problem.

Cheers,

*byronfromwesleyan*

---

