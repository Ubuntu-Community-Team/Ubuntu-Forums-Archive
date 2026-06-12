---
title: "Ubuntu can't mount itself."
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-08-12
I am almost positive this is because of VMware. I *knew* doing terminal commands while root and answering the default answers to what I am prompted would mess something up. 

Any who, I had my Windows 2000 Professional disk in the drive before I started VMware and installed Windows 2000 virtually. I took the CD out once, and Ubuntu still showed the disk on the desktop. I thought maybe Ubuntu needed a refresh. Then I realized Windows didn't come packaged with video and network drivers. I downloaded the drivers to Ubuntu and plugged in my USB to make the transfer. Windows 2000 in VMware saw it, but Ubuntu didn't. I popped in a new CD to test, and when I got it in, Windows 2000 in VMware saw it and I even played a song off of it but Ubuntu still thought I had the Windows 2000 disk in there. Shutting down VMware and refreshing and replugging the USB didn't work.

I thought a restart was in order, I shut down VMware and restarted Ubuntu. GRUB is recognized and begins to load Ubuntu. Then I see a messed up loading screen. I have a feeling Ubuntu can't mount itself or anything at all. Take a look for yourself.

[IMG]http://i13.tinypic.com/4rd0eg0.jpg[/IMG]

System Specs:
AMD Athlon 64 2800+
648MB RAM
ATI x300 256MB PCIe
Maxtor 160GB SATA hard drive, single
1 DVD-ROM drive
1 CD-ROM drive
Asus K8N4E-Deluxe Socket 754
Ubuntu 7.04

Help! :(

---

### Post by SOULRiDER on 2007-08-12
Remove the quiet and splash options from GRUB and see what kinds of errors it throws at you. To do so, select the kernel you want to load and press 'e', then delete splash and quiet (or silent, i cant remember). Then press enter and 'b' to boot. Have you tried with other kernels too?

Good luck!

---

### Post by kavon89 on 2007-08-12
I don't know what silent must have stood for, but now it works. I also figured out how VMware and sharing the USB drive between the host and virtual work.

---

### Post by SOULRiDER on 2007-08-12
Oh, good thing to hear :)

---

