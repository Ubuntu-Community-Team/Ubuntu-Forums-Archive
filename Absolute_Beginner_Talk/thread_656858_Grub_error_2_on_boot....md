---
title: "Grub error 2 on boot..."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by crispy_420 on 2008-01-03
This morning I was using my computer when I started getting random errors about file properties. Then the system locked up. I thought no big deal, Ill just restart. After a reboot, I got a Grub Error 2. Is there a way to recover the operating system, or is it toast. I looked a few solutions online and none seemed to help.This was a new install (maybe 2-3 months old) install.

Some details now. When I boot into the LiveCD, the partition seems be unformatted via GParted but command line says ext3. This leads me think this is a corrupt file system. Can that be repaired or should I do a reinstall? Is it possible to recover any of the data on it? Just a few media files is what I really care about but not having to setup from scratch would be a great bonus.

On a side note, I was not operating in any admin functionality or no sudo use. Just downloading some files . What could have happened? And what can be done to avoid this in the future?

---

### Post by rsambuca on 2008-01-03
Try using the liveCD and running a disk check on the hard drive partitions.

```
sudo fsck -f /dev/hda1
```

You will have to replace /dev/hda1 with your particular drives.

---

### Post by crispy_420 on 2008-01-03
Here is what that got me:

```
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Filesystem revision too high while trying to open /dev/sda1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

So is all lost?

Thought I would add this too:

```
 sudo fdisk -l /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f2f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

```

So it looks like there is some sort of file system present.

---

### Post by rsambuca on 2008-01-03
First, try mounting the sda1 partition from the live CD, and then you may be able to copy your media files onto a USB stick or something.  Other than that, you might try the command that it suggested:

```
sudo e2fsck -b 8193 /dev/sda1
```

---

### Post by crispy_420 on 2008-01-03
Unable to mount from LIveCD. It was giving me an error there but I am currently running e2fsck. Let's see how that turns out.

---

### Post by crispy_420 on 2008-01-04
After a little messing around with fsck and e2fsck, I was able to recover some files that I wanted but not rebuild the system. Oh well.

Thanks for the help though but the effort is too much. After all my messing around I could have just reinstalled the OS. Thank good this was my only system and that I have drive that I store my media on.

---

### Post by rsambuca on 2008-01-05
Well, it is good to hear you got at least *some* files back.  Do you have any idea whether it is your actual drive that is failing?

---

### Post by crispy_420 on 2008-01-05
I'm not sure if it is the hard drive, this is the first sign of any issues at all. But I'll keep that in mind. Even though the drive is not that old, anything can happen.

---

