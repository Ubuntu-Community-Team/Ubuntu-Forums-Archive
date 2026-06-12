---
title: "Rename mounted partition"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by SentientFluid on 2007-03-31
I used to have a file server running and had it's storage drives mounted in Ubuntu as network drives.  I recently got rid of it and added larger individual drives and set up file sharing instead of having the dedicated file server.  However, the new SATA drive I have installed in my Ubuntu machine still has the same name as the old network storage drive.  How can I change that?

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda7       /media/os_share       vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/xp    ntfs-fuse    auto,gid=1002,umask=0002    0    0
**/dev/sda1	/media/seagate320       vfat    defaults,utf8,umask=007,gid=46 0       1**
## mounting file server, but file server no longer exists. Kept for posterity
## _//192.168.1.103/Storage    /media/storage smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0_
## //192.168.1.103/Backups    /media/backups smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
```

The underlined line is the old network storage drive which is no longer in use.  It used to be called STORAGE, but the server no longer exists.

The bold line is the new SATA drive which mounts and works perfectly, except it shows up on the desktop with the name STORAGE, which I would like to change.  Right-clicking won't allow me to rename it and nothing in the fstab line mentions storage, so where does it get the name from?

Anyone know how I can change the name on the SATA drive from STORAGE to something else?

I'm running Dapper if it matters.

---

### Post by prensing on 2007-03-31
I believe the name is coming from the volume label for the partition. I am not sure how you set that on a DOS partition without reformatting, though.

---

### Post by Patrick K on 2007-03-31
No idea about XP but in Win 98, right clicking and selecting properties lets you change the volume name.

---

### Post by SentientFluid on 2007-04-01
> **prensing said:**
> I believe the name is coming from the volume label for the partition. I am not sure how you set that on a DOS partition without reformatting, though.

I didn't even think of the DOS label!

From MS-DOS you can set the label with the LABEL command at the prompt, from Windows you right-click the drive in Explorer and just type it into the volume label box.

Thanks for the reminder!

*happily heads off to make the changes*

---

