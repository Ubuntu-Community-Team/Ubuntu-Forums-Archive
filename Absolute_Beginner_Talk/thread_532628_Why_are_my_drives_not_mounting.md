---
title: "Why are my drives not mounting?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-23
I've been trying for a few days now & still can't get my drives to mount at bootup.
I've gone through all the recommended literature & still no go.
I have one computer running edgy with no problems mounting but my other one won't. 
I can run the mount command after I boot up & it works but I can't figure out why it doesn't mount at bootup.

Here's my fdisk & fstab files

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       18097   145364121    c  W95 FAT32 (LBA)
/dev/hdb2   *       18098       36246   145781842+  83  Linux
/dev/hdb3           36247       36481     1887637+   5  Extended
/dev/hdb5           36247       36481     1887606   82  Linux swap / Solaris
gary@gary-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=34c795ec-cde2-4670-b879-de9b03b4bd08 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=14535c50-0a3b-4dd4-8e62-d1cfec8278f7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/c_drive vfat   iocharset=utf8,unmask=000  0    0
/dev/hdb1    /media/d_drive vfat   iocharset=utf8,unmask=000  0    0

---

### Post by glotz on 2007-08-23
Silly suggestion but do the mount points exist? (e.g. /media/c_drive)

I've gotten burned too many times by forgetting this little step...

---

### Post by Aishiko on 2007-08-23
mount points?  please explain.

---

### Post by heimo on 2007-08-23
> **Aishiko said:**
> mount points?  please explain.

He's asking if those directories, /etc/c_drive etc. exists right after boot. That's needed for mount to work. But from your description I'd guess they do exist? How exactly do you manually mount those drives, do you need to enter device and other options, or does just "mount /media/c_drive" work as well?

---

### Post by bodhi.zazen on 2007-08-23
Add auto to your fstab options, like this :

> /dev/hda1 /media/c_drive vfat **auto**,iocharset=utf8,unmask=000 0 0
/dev/hdb1 /media/d_drive vfat **auto**,iocharset=utf8,unmask=000 0 0

---

### Post by stinger30au on 2007-08-23
dunno if this thread will help or not
[http://ubuntuforums.org/showthread.php?t=529838](http://ubuntuforums.org/showthread.php?t=529838)

---

### Post by meierfra on 2007-08-23
> /dev/hda1 /media/c_drive vfat iocharset=utf8,unmask=000 0 0
/dev/hdb1 /media/d_drive vfat iocharset=utf8,unmask=000 0 0

as far as I know it  should be "umask"  and not "unmask"

---

### Post by bigboy_pdb on 2007-08-23
> **glotz said:**
> 
... do the mount points exist? (e.g. /media/c_drive)


What he means is that there must be a directory called "c_drive" and "d_drive" in "/media". If those directories don't exist then the partitions won't be mounted. If those directories don't exist then you'll need to create them. You can do this using "sudo mkdir /media/c_drive" and "sudo mkdir /media/d_drive" in a terminal (Applications -> Accessories -> Terminal).

> **bodhi.zazen said:**
> 
Add auto to your fstab options


Just to elaborate, "auto" means that when a person uses the command "mount -a" (which means mount all), the partition will be mounted (and "mount -a" is called at boot time). Adding auto isn't necessary because the default setting for each file system is auto, but it doesn't hurt to add it.

> **meierfra said:**
> as far as I know it  should be "umask"  and not "unmask"

It should be "umask".

I would also recommend using "man fstab" and "man mount" in the command line to find out more information about the fstab file and mounting file systems. The sections that would probably be most useful to you in the manpage for mount would be "Mount options for fat" and "Mount options for vfat".

---

### Post by garyed on 2007-08-23
> **meierfra said:**
> as far as I know it  should be "umask"  and not "unmask"

Wow, that was all it took.
I thought I had copied exactly from my fstab on my other computer & never noticed "umask" instead of "unmask".
I must have checked that line a hundred times for mistakes & still never saw that.

I apologize for taking so long to get back on this but I fell asleep about 20 minutes after I posted 
& didn't get to see all the replies until the morning.

Thanks to everyone for all the help.

---

### Post by halrogers on 2007-08-23
Before we quit on this question:

I setup a scsi drive in vmware, formatted it ext2 it's /dev/sdb
I have the mount point okay

in fstab here's the line:

/dev/sdb /mnt/newdisk ext3 auto,rw,user 0 0

but here's what happens

I go to Computer, and find Filesystem, CD-ROM Drive, Floppy Drive, and 8 GB Volume

If I then double click the 8 GB Volume icon (that looks the same as Filesystem icon)
on my desktop there appears "Disk"

Okay, I guess that activated it (mounted?)

However it does NOT have rw priv for me, so i cant create any files or
directories in the drive.

Also, instead of being mounted at my /mnt/newdisk mount point, it;s
actually been mounted as /media/disk

So, is there an automatic way to

1. Have the sdb (with 1 partition, sdb1) automatically mount on bootup
2. Have it appear on the desktop as it does now but only after double clicking it
3. Have Read/Write permissions to me (not just root)
4. Predict where it will get mounted, as it doesn't go to /mnt/newdisk as i thought it might given the fact that I created /mnt/newdisk and mention it in the fstab

If I login as root the drive is right there on the desktop. But not when I login as a user.

Thanks

Hal

---

### Post by bodhi.zazen on 2007-08-23
First, it is a raw disk, or have you formated it ?

Second your fstab entry is just a little off ...

you need to add a number, like say /dev/sdb1

/dev/sdb = entire disk
/dev/sdb1 = first partition

Try :> /dev/sdb1 /mnt/newdisk ext3 auto,user 0 0

To set permissions, use chown and chmod

```
sudo chown root.users /mnt/newdisk
sudo chmod 770 /mnt/newdisk
```

---

