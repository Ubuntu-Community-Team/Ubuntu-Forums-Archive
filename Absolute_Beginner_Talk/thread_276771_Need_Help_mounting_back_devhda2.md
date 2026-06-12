---
title: "Need Help mounting back /dev/hda2"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by rlozano on 2006-10-13
i have formatted my /dev/hda2 to use vfat format, since it's using NTFS initially. i want it to be a common storage for XP and Ubuntu.

but after doing so using the GUI disk manager, i cannot enable it. i tried the cli, but i have had no luck. in both cases, i cannot mount it anymore.

can anyone suggest what to do?

thanks so much in advance.

---WindDragon---

---

### Post by Jussi Kukkonen on 2006-10-13
what's the output from *sudo fdisk -l*?
What about when you try to mount the partition?

---

### Post by dannyboy79 on 2006-10-13
> **rlozano said:**
> i have formatted my /dev/hda2 to use vfat format, since it's using NTFS initially. i want it to be a common storage for XP and Ubuntu.

but after doing so using the GUI disk manager, i cannot enable it. i tried the cli, but i have had no luck. in both cases, i cannot mount it anymore.

can anyone suggest what to do?

thanks so much in advance.

---WindDragon---
This has happened to me in the past, does it say something about bad fs type or whatever? I think it is due to bad options in your fstab. Did you forget to change the ntfs to vfat for the line in your fstab? Let's see the output of sudo fdisk -l and /etc/fstab. We'll get this fixed right away.

---

### Post by elettronicha on 2006-10-13
And, of course, post your /etc/fstab file.

---

### Post by willca on 2006-10-13
Did you create folder where to mount this to?

I recall having such problems before and the way I circumvent this was that I created a mount point. 

e.g.

mkdir /mnt/datashare

From here you can go through the disk manager gui and mount it and point it to that mount point.

Or you can also issue mount command

sudo mount /dev/hda2 /mnt/datashare


If you want to make this permanent you will need to edit your fstab. Once I see it I can possibly make a suggestion for you to try.

Cheers-
-W 8)

---

### Post by rlozano on 2006-10-13
**RESULT of fdisk -l**

randall@randall-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3387    25605688+   7  HPFS/NTFS
/dev/hda2            3388        4854    11090520    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            4865        9728    39070080    5  Extended
/dev/sda3            3825        4864     8353800   82  Linux swap / Solaris
/dev/sda5            4865        9728    39070048+   7  HPFS/NTFS

Partition table entries are not in disk order

**RESULT of /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0      1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/sda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

thanks so much in advance

---

### Post by detgar on 2006-10-13
the GUI doesn't modify your /etc/fstab to follow the change, so your new partition can't be mounted anymore, since it's a different type of FS, and the outdated fstab file still says it's the old type.

So modify your fstab file, change the old ntfs to vfat on the line that begins with /dev/hda2

---

### Post by Jussi Kukkonen on 2006-10-13
detgars advice is sound, but there's something else wrong too: look at the fdisk line for hda2:
> /dev/hda2 3388 4854 11090520 7 HPFS/NTFS
Maybe the formatting wasn't succesful...

---

