---
title: "problem with starting up ubuntu"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by deathwithafireinside on 2007-12-21
this is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a7a2d093-49a2-491a-a9f0-9046e759d41e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=421d47ac-d3fd-4120-93d9-1eb151bee847 /media/sda2     ext3    defaults        0       2
# /dev/sda5
UUID=966f1f7d-003e-4df8-8b1a-06c01f60f5c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

and this is what the checkfs says
Log of fsck -C -R -A -a 
Fri Dec 21 17:22:42 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=421d47ac-d3fd-4120-93d9-1eb151bee847'

fsck died with exit status 8

Fri Dec 21 17:22:42 2007
----------------

so this is what i see when i start
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=421d47ac-d3fd-4120-93d9-1eb151bee847'

fsck died with exit status 8

maintenance shell blah blah blah can someone help me

---

### Post by Pumalite on 2007-12-21
Did you upgrade? Did you just update? Or did you install a new system recently?

---

### Post by eternicode on 2007-12-21
Did your installation work previously?  If so, have you edited the fstab?

I believe the error is saying that the drive with UUID of "a7a2d093-49a2-491a-a9f0-9046e759d41e" doesn't exist.

Assuming you can edit the fstab, try replacing "UUID=a7a2d093-49a2-491a-a9f0-9046e759d41e" with "/dev/sda3"; duplicate the original line, comment out the first instance with a #, and modify the new line.

If you still get the error, and you're positive that sda3 is your root partition, you may be looking at a reinstall.

And if Pumalite gives advice contrary to what I give, go with that ;)

---

### Post by deathwithafireinside on 2007-12-21
> **Pumalite said:**
> Did you upgrade? Did you just update? Or did you install a new system recently?

um i installed ubuntu 7.10 a month or so ago, and there have been recent updates i really cannot say what happened but everything will help

---

### Post by Pumalite on 2007-12-21
Get to your Terminal and run:
blkid
Compare the output to that in /etc/fstab.
Take a look at your /boot/grub/menu.lst and see if everything is in order there.

---

### Post by deathwithafireinside on 2007-12-21
thank you i will try that

---

### Post by deathwithafireinside on 2007-12-21
> **Pumalite said:**
> Get to your Terminal and run:
blkid
Compare the output to that in /etc/fstab.
Take a look at your /boot/grub/menu.lst and see if everything is in order there.

uknown1@uknown1:~$ blkid
/dev/sda3: UUID="a7a2d093-49a2-491a-a9f0-9046e759d41e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="966f1f7d-003e-4df8-8b1a-06c01f60f5c3"

---

### Post by eternicode on 2007-12-21
Oh....I just realized that fsck wasn't freezing on your root...it was freezing on sda2, which is being automounted as ext3 under the /media directory.

According to your blkid output...sda2 doesn't exist...nor does sda1....which makes no sense in my mind...

What were you using sda2 for?  Any clue?

---

### Post by deathwithafireinside on 2007-12-21
i have no idea this is well beyond my technical expertise

---

### Post by Pumalite on 2007-12-21
Post:
sudo fdisk -lu

---

### Post by deathwithafireinside on 2007-12-21
uknown1@uknown1:~$ sudo fdisk -lu
[sudo] password for uknown1:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000322db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       233504775   234436544      465885    5  Extended
/dev/sda3   *          63   233504774   116752356   83  Linux
/dev/sda5       233504838   234436544      465853+  82  Linux swap / Solaris

Partition table entries are not in disk order
uknown1@uknown1:~$

---

### Post by blueridgedog on 2007-12-21
Your fstab claims you at one time had a disk mounted at /media/sda2:

UUID=421d47ac-d3fd-4120-93d9-1eb151bee847 /media/sda2 ext3 defaults 0 2

But your system sees no such partition:

/dev/sda1 233504775 234436544 465885 5 Extended
/dev/sda3 * 63 233504774 116752356 83 Linux
/dev/sda5 233504838 234436544 465853+ 82 Linux swap / Solaris

Though I would think it to be a logical and physical impossibility to create sda1, 3 and 5 without at some point making 2 and 4.

Are you missing any large chunks of files?  I would suggest that you comment out the above line in fstab and reboot.

---

### Post by eternicode on 2007-12-21
> **blueridgedog said:**
> Though I would think it to be a logical and physical impossibility to create sda1, 3 and 5 without at some point making 2 and 4.

Making sda5 without sda3 or 4 is quite possible.  Apparently, 1-4 are reserved for the primary partitions, so the first partition in the extended partition is sda5.  I'm currently working on a machine that has hda1 (primary/windows), hda2 (extended), and hda5 (logical)

It's the lack of sda2 that makes no sense in this situation... o_0

Of course, this situation seems borked....sda1 is the extended partition...and I would assume sda3 and sda5 are logicals inside of sda1....

---

### Post by deathwithafireinside on 2007-12-22
uknown1@uknown1:~$ sudo fdisk -lu
[sudo] password for uknown1:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000322db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       233504775   234436544      465885    5  Extended
/dev/sda3   *          63   233504774   116752356   83  Linux
/dev/sda5       233504838   234436544      465853+  82  Linux swap / Solaris

Partition table entries are not in disk order
uknown1@uknown1:~$

---

