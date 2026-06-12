---
title: "Where is the floppy drive in this O/S"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2005-09-29
I am trying to get on the internet with this live CD version of Unbuntu.

I think I finally perhaps found the file I need to get this O/S to recognize my modem (U.S. Robotics 56K v92 model 5610B internal - hardware).

I have copied the file onto a floppy.

How & where do I go to either run this file from the floppy drive or how do I copy this file from the floppy drive to somewhere else in the filing system so I can run this program ?

I have looked under COMPUTER which would seem to me to be the logical place to find various system drives, but the only thing I see there is the CD-Rom drive and filesystem - NO floppy drive unless I am missing something.

Thanks.

---

### Post by Buffalo Soldier on 2005-09-29
i seldom use floppy drive. but if i'm not mistaken, the icon for your floppy drive will only appear after you've inserted the disk.

---

### Post by wpshooter on 2005-09-29
I have the floppy is the drive.  I do not see it.  Is it supposed to show up under COMPUTER ?

Please note that this is the LIVE CD version of this O/S.  Is the floppy drive accessible under this LIVE CD version ?

---

### Post by mlomker on 2005-09-29
Something like this would work on a hard disk install, so give it a try in a terminal.

```

sudo mkdir /media/floppy0
sudo mount /dev/floppy0 /media/floppy0

```

It really should show up on its own, but you could try mounting it manually like that.

Have you tried posting a message to the liveCD forum?

---

### Post by wpshooter on 2005-09-29
When I run the second command it replies with "you must specify the filesystem type"

---

### Post by mlomker on 2005-09-29
[QUOTE=wpshooter]When I run the second command it replies with "you must specify the filesystem type"[/QUOTE]

**sudo mount -t vfat /dev/floppy0 /media/floppy0** 

I thought it'd autodetect it, but my laptop doesn't have a floppy so i couldn't test it.  :)

---

### Post by wpshooter on 2005-09-29
it replies floppy0 does not exit.

---

### Post by wpshooter on 2005-09-29
I found it, it needed to be fd0 instead of floppy0.

Can I run the file I have on the diskette by just clicking on it ?

Thanks.

---

### Post by mlomker on 2005-09-29
You usually can't run things from removable devices.  You should copy it to another directory first.

---

