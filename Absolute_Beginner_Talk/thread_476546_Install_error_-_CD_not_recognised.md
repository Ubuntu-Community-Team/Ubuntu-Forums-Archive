---
title: "Install error - CD not recognised??"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ahickman on 2007-06-17
I'm trying to install Ubuntu but when I boot from the CD the following heppens...

- On power up the CD is recognised, I get the Ubuntu menu and choose the default option to install
- The Ubuntu graphic with the "Kit" like red bar appears
- seems to check Floppy HD etc and then comes up with message as below

/bin/sh/ can't access tty: job control trurned off

then

(initromfs) [158.327741 ata2 port failed to respond

159.**** hub 5-0 1.0 : over current charge as port3
160.*** hub5-0 1.0 : over current charge as port4

Any advice on how to get past this. I have two "CD" devices on secondary IDE, one DVD and CDRW. I've tried making both the first to boot from in BIOS.

I also get the same message if I try to check the CD.

The CD drives can both be accessed in Windows XP.

Any advice would be much appreciated.

Thanks,
Andy

---

### Post by k33bz on 2007-06-17
im fairly new myself, i knwo a few things, very limited at that, but have you tried just running it as a live cd, and then click on the icon that says installer on the desktop?

---

### Post by ahickman on 2007-06-17
I don't think I can get far enough to have that option - I get the messages above when I choose Start or Install Ubuntu. Is there another way to run the live CD other than booting from the CD?

Thanks,
Andy

---

### Post by NfF on 2007-06-17
well u can. try booting only dvd on bios.or the CD-RW.

---

### Post by ahickman on 2007-06-17
That's all I have been doing - I've tried booting on both but get the same result with both.
Is there something else to do?

Thanks,
Andy

---

### Post by ahickman on 2007-06-17
Tried burning to another CD - same outcome. Also tried Mint Linux 3.0 with same outcome. It seems to be trying to find something on the floppy drive immediately before it gives the error message.

My thoughts are:
1) Something's wrong with my hardware/bios - I've no idea what it could be though.
2) Try to change CD player for another I have spare - not optimistic since the CRRW and DVD do work in Windows and for the first part of the boot from CD.
3) Try another non Ubuntu/Debian distribution.

Any suggestions welcome.

Thanks,
Andy

---

### Post by ahickman on 2007-06-18
Issue resolved.

Switched CDRW to Master with jumpers on the back and DVD to Slave (were previously opposite). CD then ran no problem.  Ubuntu now installed. :D

Thanks,
Andy

---

