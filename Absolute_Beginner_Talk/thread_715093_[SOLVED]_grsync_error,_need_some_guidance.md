---
title: "[SOLVED] grsync error, need some guidance"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by noremacyug on 2008-03-04
i have an external hdd that i use for backup.  i'm wanting to sync a couple of music folders.  anyhow, the external hdd is ntfs format and previously i had no issue with it working with grsync.  however, this past weekend i packed it up, took it with me and it got plugged up to a winxp computer.  when i got back home (and just had a fresh install of ubuntu) it wouldn't auto mount due to an improper shut down (didn't click the remove hardware button).  anyhow i had to use a command line to force it to read the hdd.

so now, when i attempt to use grsync to backup i get this error:

rsync: mkdir "/media/external/Music" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(529) [receiver=2.6.9]
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]


what do i need to do.  i feel that the whole issue started when the remove hardware button didn't get clicked.  does running the "force" command alter something with the hdd's permissions, etc.. and if so, how can i get it back to the original state?

as always, thanks

---

### Post by herbster on 2008-03-04
I have run into this before, your best bet is to pop it into XP and do remove hardware. You don't want to start a permissions fudge-up with it, especially when it's your backup.

---

### Post by noremacyug on 2008-03-04
will doing so negate any effects that the "force" command line had on it?

---

### Post by noremacyug on 2008-03-06
any other input on this?

---

### Post by herbster on 2008-03-06
I have used force on a USB stick some time ago after just pulling it out of the XP box, then I put it back in and it was fine. The permissions are not affected as it was an NTFS device, from what I recall. I'm pretty sure force is just "unlocking" the files temporarily as they are still owned by the XP box, so to speak. You put the device back in the XP box and it sees itself as owner again. Others may chime in and correct me but that's what I've experienced.

---

### Post by noremacyug on 2008-03-06
well, i went to plug the drive into the xp machine last night, however it's on the fritz.  sooo, i had enough room on another drive to move all my files off the external to it.  so now i'm just gonna reformat the 500gb external and start over.  how would i go about reformatting it to ntfs via ubuntu?  i have gparted installed, but the option to format to ntfs is not available.  any other programs that will allow this or will i have to be plugging it into a windows computer?

---

### Post by herbster on 2008-03-06
You can use mkntfs, or install ntfsprogs and restart Gparted, the NTFS option should be available.

---

### Post by noremacyug on 2008-03-06
> **herbster said:**
> You can use mkntfs, or install ntfsprogs and restart Gparted, the NTFS option should be available.

must appreciated!

---

### Post by noremacyug on 2008-03-06
k, got it installed and formatted to ntfs.  how do i get ubuntu to automount it and whatnot like it did previously?

---

### Post by herbster on 2008-03-06
When you plug it in, paste the output of:

```
sudo fdisk -l
```

and

```
df -h
```

Also, paste your /etc/fstab.

---

### Post by noremacyug on 2008-03-06
```
sudo fdisk -l
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeeb731cc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19128   153645628+  83  Linux
/dev/hda2           19129       19457     2642692+   5  Extended
/dev/hda5           19129       19457     2642661   82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55c46497

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   


```
df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             145G   99G   39G  73% /
varrun                442M   88K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   96K  442M   1% /dev
devshm                442M   28K  442M   1% /dev/shm
lrm                   442M   34M  408M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc              7.2G  7.2G     0 100% /media/cdrom0
/dev/hdb1             151G  112G   31G  79% /media/Storage

**/etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b57a9677-bec9-4b1b-ad6d-cd39b4c48a21 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4be03978-430b-4ba4-b14c-8ff1825d3f62 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by herbster on 2008-03-07
You should be able to use this:

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by noremacyug on 2008-03-07
k, got that.  thanks.  next issue is.... how would i change the name of the the thing?

(edit) - never mind, via further research i found my answer here ( [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) )

thanks again!!!!!  grsync is currently syncing away!!!!

---

### Post by herbster on 2008-03-07
Great to hear, glad it works :)

---

