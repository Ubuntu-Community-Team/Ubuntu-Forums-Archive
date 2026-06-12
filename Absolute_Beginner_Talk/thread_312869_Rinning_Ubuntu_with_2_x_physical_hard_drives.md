---
title: "Rinning Ubuntu with 2 x physical hard drives"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-05
For many years, my PC has used 2 x physical EIDE hard drives. They aren't arranged in a RAID array or anything. I just use the 2nd drive to make regular backup copies of the partitions on my 1st drive.

Whilst I've been evaluating Ubuntu I've left the 2nd drive disconnected (power unplugged). That's because if anything went wrong, I didn't want to risk losing my backups as well as my originals.

Now that I'm getting a bit more confident with Ubuntu, I thought I'd re-connect the 2nd hard drive - but I was surprised to find that Ubuntu doesn't realise it's there. If I boot into Windows, it sees all the partitions from both drives - but Ubuntu only sees the partitions it already knows about (namely, the ones on the first drive).

Is there some utility I need to re-run so that Ubuntu will recognise both my hard drives?

---

### Post by bodhi.zazen on 2006-12-05
> **John E said:**
> Is there some utility I need to re-run so that Ubuntu will recognise both my hard drives?

qparted with recognize your second HD and partitions.

If you did not have your 2nd HD powered up at install you will need to add it manually.

This is not difficult but it depends of the file system. I assume you have either FAT or NTFS on the second drive.

Linux uses terminology "mount"...

Let's try to mount the second HD then, in a terminal:

```
sudo mkdir /mnt/data
sudo mount /dev/hdb1 /mnt/data
```

You can call the mount point anything you like if you do not like "data".

If you want the partition on your desktop, use /media rather then /mnt (ie sudo mkdir /media/data && sudo mount /dev/hdb1 /media/data)

Now ls /mnt/data.

To make it permanent you need to edit fstab. Again, in a terminal:

```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

Add a line:> /dev/hdb1 /mnt/data auto users,umask=000 0 0

This fstab assumes your file system if FAT (vfat in Linux speak). If it is ntfs you well need to do more.

For further assistance, see [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by FuguRitual on 2007-01-08
John E, I tried bodhi.zazen's suggestion for fstab without success.  I think the problem is related to his fstab line not specifying the file system or to the unmask info.   The following worked for me as root or any user automatically:

1. Create the mount point per bodhi.zazen's direction.  You will want to use "media" instead of "mnt".   There is no need to run the mount command if what you want is to always have the drive available on boot-up.

2. Edit fstab per bodhi.zazen's direction except substitute one of the following lines:

For a Fat32 partition
```
/dev/hdb1       /media/data vfat user,fmask=0111,dmask=0000   0   0
```

For an NTFS partition (partition will be read-only)
```
/dev/hdb1       /media/data ntfs ro,user,fmask=0111,dmask=0000
```


NB: Many texts show the lines with the addition of an auto command.  Example:
```
/dev/hdb1       /media/data vfat user,auto,fmask=0111,dmask=0000   0   0
```
But it didn't seem to affect the partition recognition whether it was included or not.


3. Save and restart.

4. To mount other file systems, implement utf8, limit who can see the partition on log-in and more refer to the following:
[[COLOR="Blue"]AutomaticallyMountPartitions[/COLOR]]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").

Good Luck.

---

