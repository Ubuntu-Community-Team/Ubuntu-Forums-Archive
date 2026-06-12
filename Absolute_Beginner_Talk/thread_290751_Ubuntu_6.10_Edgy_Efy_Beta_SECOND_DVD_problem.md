---
title: "Ubuntu 6.10 Edgy Efy Beta SECOND DVD problem"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by drx0 on 2006-11-01
I added a second DVD RW to Ubuntu 6.10 Edgy Efy Beta installation and it doesn't show up (it's an NEC) (also the DVD RW used to install Edgy Beta does show up, but I can't mount any CDs or DVDs in it).  I did a cat /etc/fstab and see no entry for the new drive (I see the first drive at /dev/hdc /media/cdrom0 udf iso9660 user noauto 0 0).  The very same system running Windows all discs work fine with BOTH DVD drives (different brands) and the CDs and DVDs I'm testing with are NOT copy protected.  The GNOME mounter works for USB and Floppy disks, but not for the DVD.  Do you know how to fix this?

Thank you!

---

### Post by gitano1 on 2006-11-01
The first thing I would check when a new drive does not show up is the position of the jumper in the back of the drive. The second drive should be set as Slave and the other drive should be master. Cable select will work in some cases with a single drive, but it does not work with two drives. Make sure one of your two DVD-RW drives is master and the other is slave.

---

### Post by drx0 on 2006-11-02
The jumpers are fine.  BOTH drives work in Windows in the same system.

---

### Post by ajackson on 2006-11-02
Open a terminal and type:

ls -l /dev/dv*

If you have both a /dev/dvd and /dev/dvdrw they might be pointing to the same device because when Ubuntu is booting it asks the drives various questions (can you play dvds, can you burn dvds) trouble is both the DVD and DVD RW say they can play DVDs so Ubuntu often sets the /dev/dvd & /dev/dvdrw up wrong.

---

### Post by Thruston on 2006-11-11
Yes that's exactly the problem, but what is the answer.

I have exactly the same issue here.  /dev/hdb is a DVD-RW drive
/dev/hdc is a DVD-ROM and thanks to udev I get

lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/dvd -> hdb
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/dvdrw -> hdb
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/cdrom -> hdb
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/cdrw -> hdb

instead of the sensible alternative of 
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/dvd -> hdc
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/dvdrw -> hdb
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/cdrom -> hdc
lrwxrwxrwx 1 root root 3 2006-11-11 14:29 /dev/cdrw -> hdb
 
How can I get udev to do this please?  Would it help to swap them round on the IDE bus?  

T.

---

