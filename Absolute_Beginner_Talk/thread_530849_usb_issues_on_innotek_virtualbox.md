---
title: "usb issues on innotek virtualbox"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by welder73 on 2007-08-20
I 've got xp running in the box so i can use the software that came with my gps.  But when i go to transfer to or from the gps unit. i get this error window.

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

being new to Ubuntu i'm not sure what to do in terminal to fix this.    Trashing xp  was the best thing i've for my sanity.    UBUNTU ROCKS

---

### Post by AcworthJack on 2007-08-20
Sorry - I have never tried Virtual box (I have used VMWare with some success - although performance can be an issue).

I found this on the V.B. web: [http://www.virtualbox.org/ticket/60](http://www.virtualbox.org/ticket/60)
It may give you some pointers in the right direction.
I am fairly new to Ubuntu but this doesn't seem to be a Ubuntu issue as far as I can tell.

Good luck,
John

---

### Post by Joakim Stokland on 2007-09-02
Figured it out yet?
You need to give VirtualBox permissions to the USB port. I don't remember exactly how you do that, but for a starter you could run VirtualBox as root (sudo VirtualBox [and remember to use capital V and B in VirtualBox])

---

