---
title: "[SOLVED] ntfs signature is missing"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2008-03-11
I can't mount my external USB HD. It was honestly working about 15 min ago and now it's kaput.... I *need* the data on that drive, I recently swapped out my internal HD and this is the only backup I have for the last 5 years...

Here's what I've tried so far...
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1720aca6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1/ /mnt/temp
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

then I thought perhaps it was HPFS (whatever the heck that is)
```
ubuntu@ubuntu:~$ sudo mount -t hpfs /dev/sdb1/ /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

here is output of **dmesg | tail**:
```
ubuntu@ubuntu:~$ dmesg | tail
[ 1993.832000] sd 9:0:0:0: [sdb] Write Protect is off
[ 1993.832000] sd 9:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1993.832000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1993.832000]  sdb: sdb1
[ 1993.840000] sd 9:0:0:0: [sdb] Attached SCSI disk
[ 1993.840000] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 2127.184000] HPFS: bad mount options.
[ 2174.140000] HPFS: bad mount options.
[ 2480.996000] HPFS: bad mount options.
[ 2750.408000] HPFS: Bad magic ... probably not HPFS
```

As  i mentioned before... I really need this info, any help anyone?

---

### Post by bumanie on 2008-03-11
Were you using it on windows prior to plugging it in to ubuntu? If so are you sure you removed it correctly by stopping it? If not, ubntu won't read it. Boot back in to windows and stop the device properly and then ubuntu will read it. If my assumption is wrong, I don't know why it would suddenly stop.

---

### Post by Oldsoldier2003 on 2008-03-11
> **bumanie said:**
> Were you using it on windows prior to plugging it in to ubuntu? If so are you sure you removed it correctly by stopping it? If not, ubntu won't read it. Boot back in to windows and stop the device properly and then ubuntu will read it. If my assumption is wrong, I don't know why it would suddenly stop.

and mount it as NTFS, not HTFS

---

### Post by tango_ninja on 2008-03-11
Yes it was previously used on Windows...about 30 min ago and it worked fine. It can't be read on windows anymore either....says it needs to be formatted.

It sounds like the drive is in trouble...but i honestly need that data, it's my only backup in the last 5 yrs......

---

### Post by tango_ninja on 2008-03-11
> **Oldsoldier2003 said:**
> and mount it as NTFS, not HTFS

you'll see (above) I tried both...

---

### Post by Oldsoldier2003 on 2008-03-11
> **tango_ninja said:**
> you'll see (above) I tried both...

yes, that was in conjunction with the advice to do a clean shutdown. even if you had done a clean shutdown trying to remount as HPFS would result in a failed mount.

---

### Post by bumanie on 2008-03-11
If it isn't working on windows either, it sounds very ominous - drives do have a finite life unfortunately. If it is the drive (bearings or whatever) there's not much you can do. I have heard of people placing drives that have gone kaput into the fridge for a couple of hours (wrapped in a towel to stop moisture) and finding they can get half an hour so to copy info. before it seizes again. Never tried it myself. No guarantee that it'll work. But if your drive doesn't fire up, it may be worth keeping in mind as a last resort. In the mean-time prepare a drive or partition so that if it does fire up at some point, you can save the data immediately.

---

### Post by tango_ninja on 2008-03-11
> **bumanie said:**
> If it isn't working on windows either, it sounds very ominous - drives do have a finite life unfortunately. If it is the drive (bearings or whatever) there's not much you can do. I have heard of people placing drives that have gone kaput into the fridge for a couple of hours (wrapped in a towel to stop moisture) and finding they can get half an hour so to copy info. before it seizes again. Never tried it myself. No guarantee that it'll work. But if your drive doesn't fire up, it may be worth keeping in mind as a last resort. In the mean-time prepare a drive or partition so that if it does fire up at some point, you can save the data immediately.

thanks bumanie. i might give it a try :)

I found an winXP program (I dual boot XPpro) called "Recover my Files" and it's currently searching my partition for my most important files (.jpeg .mp3 .doc .xls). hopefully it will work out

thanks guys, if anyone has any fresh ideas please let me know!

---

### Post by gobuntu on 2008-03-11
Tango Ninja,

If your drive is NTFS formatted (Windows XP) or so:

I strongly recommend you install ntfs-config via synapsis without the drive plugged in.

Then from Applications/System Tools run NTFS Configuration tool.

Its instructions on what follows should be quite clear and easy to do.

---

### Post by tango_ninja on 2008-03-12
ah yes... i had forgotten to mention i had already installed ntfs-config. didn't do anything helpful though :(

---

### Post by bumanie on 2008-03-12
You could try test disk it's a partition/data recovery program. If it can read the hard drive, it has a reasonable chance of recovering most of your information. But I can't see how it will work if the drive isn't working, however if the drive is spinning, it should work. If the drive is spinning it is more likely to be a file system corruption or something like that. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by gobuntu on 2008-03-12
Hi ninja,

Perhaps the disk is not NTFS formatted? 

You say "five years of data" somewhere above, and maybe that disk is FAT-32,  in which case NTFS-conf does not apply.

Your Windows system does not read it? What version is it?
Maybe Windows-XP system can fix it via the Administrative tools?

---

### Post by tango_ninja on 2008-03-12
The disk was definitely NTFS formatted.... the 5 yrs of data was from various sources, all stored on the drive.

I ended up having to re-format it but managed to get most of the data back from an older corrupt drive. thanks everyone for your help.

---

