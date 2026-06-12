---
title: "[SOLVED] Unable to mount media"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-24
After sudo-ing:

sudo mount -a

my dvd reader (which has a dvd in it from boot) returns the usual:

Unable to mount media

Here is my /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a70ca0f-767b-4efb-8d00-7b5c800098d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=89e97a5c-4907-46f4-80eb-376f871c1d49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I just don't know where the problem is.

---

### Post by mahiyar on 2007-11-24
Can you remove the media and put some other disk in it?

---

### Post by Mark_in_Hollywood on 2007-11-24
same story: unable to mount media.

The media is: a commercial educational dvd, played on my tv set via it's own dvd machine (not compter connectable)

---

### Post by Pumalite on 2007-11-24
Sudo apt-get install ubuntu-restricted-extras
And add Medibuntu to your repositories and install all the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by Mark_in_Hollywood on 2007-11-24
This is a problem with mounting, not with codecs. They have already been installed.

---

### Post by jingo811 on 2007-11-24
It might be something wrong with your particular CD.  Try putting in some regular music CD or some Data backup CD instead for testing. ( Wrong but not broken, mind you! )

I had a similar problem when trying to read my DVD-rw discs Ubuntu couldn't recognize and mount those discs.  But when I put in some regular DVD-r discs and music CDs etc. Ubuntu could mount the CDROM drive again.

---

### Post by Mark_in_Hollywood on 2007-11-24
Done and

Done

before I made my first post on this thread

---

### Post by JBAlaska on 2007-11-24
If you already have libdvdread3 and libdvdcss2 installed, try;
```
sudo mount /media/cdrom0/ -o unhide
``` where "cdrom0" is your dvd device name.

---

### Post by Mark_in_Hollywood on 2007-11-24
How would that matter? I did a sudo mount -a

and still could not get the drive to "see" the media

yet, on trying the command suggested:

mark@Lexington:~$ sudo mount /media/cdrom1/ -o unhide
[sudo] password for mark:
mount: No medium found

---

### Post by Mark_in_Hollywood on 2007-11-24
Is there a way to see if the "drivers" are installed for this device? Looking through System/Preferences/HardwareInformation I see everything listed except my CD and DVD. The CD works, why not the DVD? And why aren't they listed along with all the rest of the hardware?

---

### Post by Pumalite on 2007-11-24
Go to /dev and see if you have a device there.

---

### Post by Mark_in_Hollywood on 2007-11-24
As best as I understand that always full directory:

cdrom    
cdrom1
cdrw
dvd1

that's all I saw that was optical drive related. But I'm guessing there is a huge list of files, mostly tty-s.

---

### Post by Mark_in_Hollywood on 2007-12-07
The optical drive had "broken". There was no way to know. The drive's led flashes on media being put in the tray and the tray door closed. The eject switch works.

Please accept this apology.

---

### Post by wmichaelb on 2007-12-07
Was the master/slave jumper set correctly?

---

