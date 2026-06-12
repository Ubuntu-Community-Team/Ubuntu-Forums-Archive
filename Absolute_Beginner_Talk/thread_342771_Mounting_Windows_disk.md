---
title: "Mounting Windows disk"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-01-20
Hi probably a real newbie question but I'm a bit stuck trying to get edgy to see my windows drive.  I'm following the method on [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) and using /etc/fstab file.

Got to the point pasted below and I'm a bit confused as to what to do next


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5b7e0230-e5ca-4d58-b951-4fdef9abdfc8 /               ext3    defaults,erro$
# /dev/sda8
UUID=9f718fc5-fd1c-4ac1-8ac0-c16bb780ece0 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Can anyone guide me forward from here please?

---

### Post by taurus on 2007-01-20
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by bugster on 2007-01-20
Wow that was quick thanks - here's the result

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15201   122102001    7  HPFS/NTFS
/dev/sda2           15202       30401   122094000    f  W95 Ext'd (LBA)
/dev/sda5           15202       16612    11333826    7  HPFS/NTFS
/dev/sda6           29598       30401     6458098+   b  W95 FAT32
/dev/sda7   *       16613       29409   102791871   83  Linux
/dev/sda8           29410       29597     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2007-01-20
I assume you want to mount /dev/sda1, /dev/sda5, & /dev/sda6.

Open a terminal and edit your /etc/fstab.

```
gksudo gedit /etc/fstab
```
Add these three lines to the end of it.

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   ntfs   nls=utf8,umask=0222   0   0
/dev/sda6   /media/sda6   vfat   iocharset=utf8,umask=000   0   0

```
Save the changes.  Now, create three new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda5 /media/sda6
sudo mount -a
df -h
```

---

### Post by bugster on 2007-01-20
Thanks Taurus - willdo - I'll let you know the result.

---

### Post by bugster on 2007-01-20
Thanks a million Taurus - it went like a dream - you are a STAR ):P ):P

---

### Post by taurus on 2007-01-20
Probably just a lucky guess!  ;)

---

