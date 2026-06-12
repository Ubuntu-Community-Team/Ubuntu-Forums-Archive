---
title: "[SOLVED] accessing external drive from command line?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-20
How can I access my external USB harddrive from recovery mode command-line only? I need to back up some files and do a reinstall, and I cannot access my GUI without it freezing.:confused::popcorn:

---

### Post by forrestcupp on 2008-03-20
Type:
```
cd /media
ls -a
```
to see what drives are available.  Then you can cd into the right one and access the files on it.

---

### Post by philosophicscience on 2008-03-20
all i am getting: ```
 cdrom cdrom0 
```
it doesnt seem to be showing the drive, any suggestions?

When I unplug and plug in the hard drive I get a message that says:
```

[  482.404000] sd 3:0:0:0: [sdb] Assuming drive cache: write through

[  482.408000] sd 3:0:0:0: [sdb] Assuming drive cache: write through

```

---

### Post by philosophicscience on 2008-03-20
did this: 
```
sudo fdisk -l
```

and got this:

```
 Disk /dev/sda: 120.0 GB 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf8550f6


   Device Boot   Start    End    Blocks   Id   System
/dev/sda1       xxxxxxxxxxxxxxxxxx
/dev/sda2       xxxxxxxxxxxxxxxxxxxxxxx
/dev/sda5       xxxxxxxxxxxxxxxxxxxxxxxx

Disk /dev/sdb: 250.0 GB XXXXXXXXXXXXXXX bytes
255 heads, 63xxxxxxxxxxxxxxxxx
units xxxxxxxxxxxxxxxxxx
Disk identifier: 0xa4b57300

Device boot start end blocks id system
/dev/sdba 1 xxxxxxxxxxxxxxxxxxx


```

I'm typing this all by hand from another computer, :(. 

Help :confused:

The x's are unimportant seeming numbers and such, I can fill them in if needed. How do I copy files to this dir? when I tried to ls /dev/sdb1 it says does not exist. my external is a seagate 250 gb so that should be it.

---

### Post by bodhi.zazen on 2008-03-20
You can either pmount or mount.

```
pmount /dev/sdb1 sdb1
```

This should mount the device at /media/sdb1

Or use mount.

```
mount /dev/sdb1 /mnt
```

That will mount the device at /mnt

If for some reason you are not root, use sudo with the mount command (pmount can be run as a user)

---

### Post by philosophicscience on 2008-03-20
```
 mount /dev/sdb1 /mnt
```

gives me
```
 $logfile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have windows then disconnect the external devices by clicking on the 'Safely' yah yah not applicable

Choice 2: if don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: 
    mount -t ntfs-3g /dev/sdb1 /mnt -force
or add the option to the relevant row in the /etc/fstab file:
    /dev/sdva /mnt ntfs-3g degaults, force 0 0


```

What next?

edit: I did the first piece of code and it gave me 

```

$LogFile indivates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

```

---

### Post by philosophicscience on 2008-03-20
Update!!

I cd to /mnt and now all of the contents of my external are displayed in green writing. How can I copy files from my harddrive to here? Preferably folder at a time and not file at a time. Thanks!

---

### Post by bodhi.zazen on 2008-03-20
cp -R <source> <destination>

so

```
cp -R /mnt/dir_to_copy /location_to/copy_to
```

---

### Post by philosophicscience on 2008-03-21
Alright, figured that one out. Seems to be working except for a few files that read Invalid or incomplete multibyte or wide character

---

