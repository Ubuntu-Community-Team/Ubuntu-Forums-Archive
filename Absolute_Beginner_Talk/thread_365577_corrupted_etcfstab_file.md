---
title: "corrupted /etc/fstab file"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-02-19
I just have reinstalled Ubuntu and tried to mount NTFS drive with Automatic Mount. That did not work as I still cannot find my XP that I have on a separate drive.
I now was told that my /etc/fstab file is corrupted. I am still new to Linux and do not have a clue what to do. Could somebody please help me. This is a copy.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c9629ae0-2533-4d18-a492-96ce25caa8fc /               ext3    defaults,erro$
# /dev/hda5
UUID=906e0517-9e50-4f18-88c7-e34ad9b53fa9 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs-fuse rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs-fuse rw,user,fmask=0111,dmask=0000 0 0

Thanx in advance:)

---

### Post by taurus on 2007-02-19
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Chamelion on 2007-02-19
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9359    75176136   83  Linux
/dev/hda2            9360        9733     3004155    f  W95 Ext'd (LBA)
/dev/hda5            9360        9733     3004123+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3807    30579696    7  HPFS/NTFS
/dev/sda2            3808       10885    56854035    f  W95 Ext'd (LBA)
/dev/sda5            3808       10885    56854003+   7  HPFS/NTFS

---

### Post by po0f on 2007-02-19
Chamelion,

Unless it was a typo, these lines:

```
[FONT="Courier New"]UUID=c9629ae0-2533-4d18-a492-96ce25caa8fc / ext3 defaults,erro$
UUID=906e0517-9e50-4f18-88c7-e34ad9b53fa9 none swap sw $[/FONT]
```

should probably read:

```
[FONT="Courier New"]UUID=c9629ae0-2533-4d18-a492-96ce25caa8fc / ext3 defaults,errors=remount-ro 0 1
UUID=906e0517-9e50-4f18-88c7-e34ad9b53fa9 none swap sw 0 0[/FONT]
```

And what do you mean by "Automatic Mount"?  If it's a program, I haven't heard of it.  And please post the exact error you are getting; if it's from a GUI application, please post a screenshot.

---

### Post by Chamelion on 2007-02-19
The automatic mounting :

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-e070ee95af2fd63663dff08b8fd783f429bc29a5](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-e070ee95af2fd63663dff08b8fd783f429bc29a5)
 
Still does not work.

---

