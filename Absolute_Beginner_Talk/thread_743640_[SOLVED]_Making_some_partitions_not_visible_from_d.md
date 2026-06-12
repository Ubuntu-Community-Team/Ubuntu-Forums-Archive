---
title: "[SOLVED] Making some partitions not visible from desktop and file browser."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Bellicus on 2008-04-02
I got 3 partitions of my harddrive visible on the desktop. One is for windows and program files, one is for windows games and stuff, and one for ubuntu. The only one i'm really interested in having visible is the ubuntu partition, then i would feel safer not to mess anything up by mistake. when i try to unmount the partitions i get a error messege telling me i'm not priviliged to unmount the volume. "only root can unmount", but i dont even know what root is.

---

### Post by cardinals_fan on 2008-04-02
> **Bellicus said:**
> I got 3 partitions of my harddrive visible on the desktop. One is for windows and program files, one is for windows games and stuff, and one for ubuntu. The only one i'm really interested in having visible is the ubuntu partition, then i would feel safer not to mess anything up by mistake. when i try to unmount the partitions i get a error messege telling me i'm not priviliged to unmount the volume. "only root can unmount", but i dont even know what root is.
**How are you trying to unmount them?**  FYI, root is the Linux 'super-user'.  It is the only one who can control important system settings.  Whenever you run a command with 'sudo' you are temporarily using the root account to execute a command.  This is whenever you are asked for the administrative password.

---

### Post by Bellicus on 2008-04-02
> **cardinals_fan said:**
> [B]How are you trying to unmount them?[/B.

From file browser and desktop by rightclicking.

I don't know any commands for doing this.

---

### Post by Moop on 2008-04-02
In the terminal type ```
gksudo nautilus
``` the file browser window will open and you can unmount them from there.

---

### Post by Bellicus on 2008-04-02
> **Moop said:**
> In the terminal type ```
gksudo nautilus
``` the file browser window will open and you can unmount them from there.

When using that command i'm getting a file browser where the volumes i want to unmount are not visible. :-?

---

### Post by Moop on 2008-04-02
Look for them in the File System. They should be in the media directory (folder).

---

### Post by Bellicus on 2008-04-02
> **Moop said:**
> Look for them in the File System. They should be in the media directory (folder).

I found them, but they are folders, and I can't find any way to unmount them.

---

### Post by Bellicus on 2008-04-03
Bump, still no idea how to make these partitions not visible.

---

### Post by Bellicus on 2008-04-03
One last bump.

Anyone know how to unmount these partitions?

---

### Post by forestpixie on 2008-04-03
Are you trying to make it so that the ntfs (windows) partitions don't mount at all - so that you're buntu and windows installations are completely seperate from each other and data can't be shared?

IF so can you open a terminal and paste the outputs here from these 2 commands

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Bellicus on 2008-04-03
> **forestpixie said:**
> Are you trying to make it so that the ntfs (windows) partitions don't mount at all - so that you're buntu and windows installations are completely seperate from each other and data can't be shared?

Yes, thats what i want :)

---

### Post by ryanhaigh on 2008-04-03
You can stop these partitions from being mounted at boot by removing them from /etc/fstab (or just comment them out incase you ever do need them). You should be able to figure out which lines correspond to the drives by looking at the mount point used and add a # to the start of those lines. 

If you want to do this temporarily open a terminal and use ```
sudo umount /media/partitionnamehere 
```. You could actually make a launcher on your desktop for that as well by right clicking on the desktop>new launcher and use the command ```
gksudo umount /media/partitionnamehere
``` gksudo will popup a password box like when starting an admin app.

If you just don't want the icon on the desktop there is no way to have just some of the volumes you can however stop any volumes showing up by changing a setting in gconf-editor, search for volumes visible IIRC and uncheck.

---

### Post by tangibleorange on 2008-04-03
To unmount a partition from the terminal:

```
sudo umount /dev/sda*
```

where * is the partition you wish to unmount. you can find a list of your partitions with this command:

```
cat /etc/fstab
```

---

### Post by forestpixie on 2008-04-03
Ok can you post the output of those 2 commands - we can edit the file which mounts the ntfs partitions and they will not be available in ubuntu.

---

### Post by Bellicus on 2008-04-03
Great, the ntfs partitions are gone from the desktop now, and i got no access to them from the file browser, so no worries about messing stuff up now. Thanks a alot guys :)

---

### Post by Bellicus on 2008-04-03
> **forestpixie said:**
> Are you trying to make it so that the ntfs (windows) partitions don't mount at all - so that you're buntu and windows installations are completely seperate from each other and data can't be shared?

IF so can you open a terminal and paste the outputs here from these 2 commands

```
sudo fdisk -l
cat /etc/fstab
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ca553df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020       30930   240259072    6  FAT16
/dev/sda3           31624       60801   234372285   83  Linux
/dev/sda4           30931       31623     5566522+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6677085f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    f  W95 Ext'd (LBA)
/dev/sdb5               1       60802   488383488    7  HPFS/NTFS
administrator@administrator-desktop:~$ 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=31ef4a35-8e3d-4b9f-883b-9c52d5a883cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=76043434E49BED2A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=62A8E0F1A8E0C51F /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4A90D5C590D5B821 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=55957354-80f9-499e-a7fa-47506e0dc95a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
administrator@administrator-desktop:~$

Sda1 sda2 and sdb5 is the ones i used umount on.

---

### Post by forestpixie on 2008-04-03
If you want to stop mount on reboot - backup the file just in case and edit the fstab
```

sudo cp /etc/fstab /etc/fstab.0304
gksudo gedit /etc/fstab

```
edit these lines and put a # in front of the UUID
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=31ef4a35-8e3d-4b9f-883b-9c52d5a883cc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
[COLOR="Red"]#UUID=76043434E49BED2A /media/sda1 ntfs defaults,umask=007,gid=46 0 1[/COLOR]
# /dev/sda2
[COLOR="Red"]#UUID=62A8E0F1A8E0C51F /media/sda2 ntfs defaults,umask=007,gid=46 0 1[/COLOR]
# /dev/sdb5
[COLOR="Red"]#UUID=4A90D5C590D5B821 /media/sdb5 ntfs defaults,umask=007,gid=46 0 1[/COLOR]
# /dev/sda4
UUID=55957354-80f9-499e-a7fa-47506e0dc95a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

---

