---
title: "Mounting Windows Partition after Windows Reinstall"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by AnthoMacP on 2007-10-13
I seem to be having an issue getting my windows drive to automount or really mount at all correctly. I decided a while ago to delete my /dev/sda1 which was a dell utility partition (useless to me) and recently reformatted my windows partition which was previously /dev/sda2 and to take up the extra space the dell utility partition was using aswell since i was reformatting the windows partition anyway. The reinstall went perfectly and i reenabled grub (hd0,1) for my ubuntu partition and (hd0,0) for my windows partition and both boot perfectly. The problem I'm having seems to be something related to fstab but i can't quite figure it out. my fdisk -l output is below aswell as my current fstab settings. I also have 2 externals plugged in if that matters at all (shouldn't)
sudo fdisk -l

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5621    45150651    7  HPFS/NTFS
/dev/sda2            5622        7220    12843967+  83  Linux
/dev/sda3            7221        7295      602437+   f  W95 Ext'd (LBA)
/dev/sda5            7221        7295      602406   82  Linux swap / Solaris

```
sudo gedit /etc/fstab
```

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=175f763e-d797-4be9-b2a3-f7a384cf85cb / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=07D4-0617 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=0258184A58183F3B /media/sda2 ntfs-3g defaults,locale=en_CA.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=78cddf1a-a1d7-48cf-921a-084bffd1d8f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Any help would be great as i use my NTFS as my music and work storage drive and I can't properly access it now. Also, it's probably worth noting that i can go into Places>Computer and mount it as disk-1 and view the data but it still refuses to automount.

---

### Post by alienexplorers on 2007-10-13
You have sda2 listed twice.  Is this correct?

---

### Post by logos34 on 2007-10-13
> proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=175f763e-d797-4be9-b2a3-f7a384cf85cb / ext3 defaults,errors=remount-ro 0 1
[COLOR="Red"]# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=07D4-0617 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=0258184A58183F3B /media/sda2 ntfs-3g defaults,locale=en_CA.UTF-8 0 1[/COLOR]
# Entry for /dev/sda5 :
UUID=78cddf1a-a1d7-48cf-921a-084bffd1d8f6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

Take out the stuff in red.  Replace windows entry with:

> [COLOR="Blue"]/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_CA.UTF-8 0 1[/COLOR]

or
> 
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

(if you use the latter you'll have to run ntfs-config again to enable write support).

edit: You can also delete the mountpoint /media/sda2 since you won't be needing it anymore (linux root is now sda2 and mounts at '/')

**sudo rmdir /media/sda2**

---

### Post by AnthoMacP on 2007-10-13
thanks logos, that fixed it.

---

