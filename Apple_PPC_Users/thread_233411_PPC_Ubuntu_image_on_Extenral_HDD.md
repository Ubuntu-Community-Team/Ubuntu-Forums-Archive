---
title: "PPC Ubuntu image on Extenral HDD"
date: 2006-08-10
forum: Apple PPC Users
---

### Post by Waste on 2006-08-10
Hi, I know this may be a weird request for help, but I really need to know if this can be done.
I have an older iMac with a broken CD drive. (Picked it up off ebay for $20. :) )
What I want to figure out how to or if it's even possible, is to see if I can ghost the PPC Ubuntu CD onto an exteranl USB drive and boot my Imac onto to it to install Ubuntu that way.
I really am trying to avoid paying $100 for a replacement drive since I only paid $20 for this iMac.
All I want to do is get it to run as a light webserver from my home.


Any help is much appreciated.

Thanks,
Clint

---

### Post by 3rdalbum on 2006-08-10
It depends how old the iMac is. Most of the older iMacs cannot boot from USB. If it's a tray-loader with the CD laser actually built into the tray, then it can't do a USB boot. If it's a slot-loader, it might be able to. If it's any other iMac, you would have to boot from Firewire, not from USB.

I believe the CD has documentation about how to boot the Ubuntu CD from an external USB drive; you'll want to consult that. 

Don't open the .iso file on the Mac though, as it will damage the file (if you must open the .iso to look at the documentation, do it on a backup).

If you want to run a simple, static web server on your Mac, you can still do that with whatever Mac OS version you have plus an Apple program called "Personal Web Sharing", or WebSTAR (formerly known as MacHTTP).

---

### Post by Waste on 2006-08-10
The problem is, it has no OS on it.
It had OS8 on it when I got it, but in attempt to upgrade it to something more modern, that's when the CD drive died. 

The CD is a tray loader similiar to a laptop cd drive, i.e. the non powered ones where you push the button and it pops out, but you have to pull it the rest of the way out.

And it doesn't have Firewire on it. :(

---

### Post by avtolle on 2006-08-10
You may have a problem without an OS; it sounds like an "Old World" Mac; to install Ubuntu thereon requires, at a minimum, a Mac OS with Boot-X, this problem in addition to those already described by 3rdalbum. By the way, there is an alternative to Boot-X whose name escapes me, but from my recollection, is somewhat inconsistent in whether it works.

---

### Post by Waste on 2006-08-10
Well, in that case, could a Mac OSX image be put onto the external drive and use it to install from that?
I have a CD and DVD version of OSX 10.2 somehere.

---

