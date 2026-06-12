---
title: "External HDD"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-09-24
Hey everybody,

For some reason Ubuntu isn't recognizing my external hard drive.  I have a Seagate FreeAgent Pro, and it's plugged into a USB port on my computer.  I have it formatted in ntfs with ntfs 3g installed.  At first, when I ran the gparted live cd, it was recognized, but now even that can't spot it.  Any ideas?

Thanks,

Helixed

---

### Post by Pumalite on 2007-09-24
Fiddle with your BIOS.

---

### Post by helixed on 2007-09-24
Well it worked fine in Windows...  I don't really know what fiddling with my bios would do.

Helixed

---

### Post by Pumalite on 2007-09-24
Is your External recognized by your BIOS?

---

### Post by helixed on 2007-09-24
Honestly, I don't really see any options in my bios setup which would acknowledge my external hdd.  I'm running a Dell e1705.  This is really strange, because in a previous install, I had it running fine.

Thanks,

Helixed

---

### Post by Pumalite on 2007-09-24
Get you hard drive out of the box, connect it internally to another computer and check it.

---

### Post by helixed on 2007-09-24
Uh, I can't connect it internally to another computer.  it's an external hard drive...

---

### Post by expatCM on 2007-09-25
I think what Pumalite means is either -

*  Take the external drive to another computer and test it there.
or
*  Take the drive out of the housing and then plug the drive into the computer as an internal drive.  Depending on the type of drive you may need to change the jumper settings to Slave when you do this.  If it is a SATA drive then you will need not worry about the jumper.

You may also want to plug it into another USB port since sometimes the drive is then detected (but possibly not mounted).

---

### Post by helixed on 2007-09-25
Plugging it into another usb port seemed to fix the issue.  I was reading on a forum how this particular drive has issues with Linux because of something called spin down.  I'm not sure if that had anything to do with this, but oh well, it works now.

Thanks for the help.

Helixed

---

