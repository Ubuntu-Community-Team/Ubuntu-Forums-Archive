---
title: "VMWare Server using HD partitions"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by RoflCake on 2007-08-26
When I try to use a physical FAT32 disk partition as the disk for VMWare, it gives me the error
> Failed to load partitions for device /dev/hda: Permission denied
Do I have to unmount the drive or something? Also, will VMWare run seamlessly in this fashion?

---

### Post by VSpike on 2007-08-26
You need to get permissions on the device itself.  I think the easiest way is to do:

sudo adduser <yourname> disk

You'll need to log out and back in again.

If that doesn't work, try chmod o+rw /dev/hda or whatever the device is.  You may need to do the parition(s) too, e.g. /dev/hda1

I used to do this, but actually I don't recommend this setup.  You should not have the partition mounted by Ubuntu if you want to do direct access from VMWare, otherwise you will get file system corruptions and wierd problems.

If you want to share data with VMware, share the partition using SAMBA or NFS.  You'll still need a native VMWare boot parition, but data can be shared like this.

---

### Post by RoflCake on 2007-08-26
Thanks for your reply, however, I have a new question. I can resize my NTFS partition as much as I wish, but I can't resize the partition Ubuntu is installed on? How am I, then, supposed to delete my XP partition and resize my Ubuntu partition to take up the unallocated space? When I try to unmount the ext3 partition using GParted it returns:

> The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.
and I'm pretty sure I can't unmount the swap partition.

Then when I try to do 'umount' in terminal it gives this:

> sudo umount /dev/hda2
umount: /: device is busy
umount: /: device is busy


---

