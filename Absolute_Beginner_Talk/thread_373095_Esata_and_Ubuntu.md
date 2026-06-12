---
title: "Esata and Ubuntu"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by yochaigal on 2007-02-28
Hi.  I have a nextstar esata/usb external hard drive.
i can easily recognize and mount the drive using the usb interface.  i cannot with esata.  I am sure I have it setup correctly; i  used it on a previous xp installation.
when i plug it in, it does nothing.  nothing in fdisk or fstab.  
any ideas?  
thanks.

---

### Post by actuary286 on 2007-03-01
Unfortunately, Linux won't automatically detect an eSATA drive because it is like adding a new internal hard drive to the system. You will have to manually edit your fstab to add an entry for it.

---

### Post by yochaigal on 2007-03-01
What should i put in fstab?

thanks!

---

### Post by lex on 2007-04-12
> **actuary286 said:**
> Unfortunately, Linux won't automatically detect an eSATA drive because it is like adding a new internal hard drive to the system. You will have to manually edit your fstab to add an entry for it.
I would also like to know how to edit the fstab. Please explain for an absolute beginner?
Basically I want to use an external eSata HHD but have no idea about how to go about it. Any help would be much appreciated.
Thanks:)

---

### Post by yochaigal on 2007-04-13
It's actually easy!  Just get feisty (even beta stage is fine... or  wait till the 17th).
It works fine with the new kernel (2.6.20.14).  Just remember,  it treats your drive as a real drive, not an external usb device.  So edit the fstab preferences to match that of a normal drive (non-filesystem, of course).

---

### Post by yochaigal on 2007-04-16
this is what my fstab entry looks llike:
it allows full access and automount upon drive-shutoff.

/dev/sda1                                  /media/disk     ext3         errors=panic,users          0  0

---

