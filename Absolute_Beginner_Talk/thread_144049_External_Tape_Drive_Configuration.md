---
title: "External Tape Drive Configuration"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Mike S. on 2006-03-13
Hi:

I have an HP Colorado 20GB external Travan tape drive model
C4448A that I'd like to use with my file server.  The tape drive connects via the parallel port of the computer.

I'm using version 5.10 of Ubuntu.

Only Windows drivers appear on HP's Website.

Does anyone know if I can use the tape drive and in addition how do I make a driver for it?

Thanks,


Mike

:)

---

### Post by Pragmatist on 2006-03-16
I'm guessing the drive connects using a parallel port?

I don't think that model is supported, though other HP Colorado models are, like the T-1000.  Go figure.

[http://www.tldp.org/HOWTO/Ftape-HOWTO-6.html](http://www.tldp.org/HOWTO/Ftape-HOWTO-6.html)
[http://cyberelk.net/tim/parport/parport.html](http://cyberelk.net/tim/parport/parport.html)

---

### Post by Kadin2048 on 2006-03-24
I'm currently struggling to set up a SCSI tape drive (which ought to be easier than a parallel port one, in theory) and having trouble...

Anyway when I was looking for info on SCSI drives I ran across some parallel and floppy-port tape stuff, thought I'd put it out here. Maybe it will help you.

I think what you need for a parallel port tape drive is the "ftape" utility:
[http://packages.ubuntulinux.org/warty/utils/ftape-util](http://packages.ubuntulinux.org/warty/utils/ftape-util)

It says "Some parallel port tape drives are also supported, too. These are the Colorado Trakker and several kinds of parallel port drives that use the Micro Solutions' "Backpack" protocol, i.e. the Iomega Ditto parallel port drives, and some parallel port floppy tape drives made by Exabyte and Seagate.""

Good luck.

---

