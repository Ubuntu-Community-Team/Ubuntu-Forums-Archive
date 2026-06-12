---
title: "[Kubuntu] How can I change the name/label of my harddrives?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Crakie on 2006-11-18
Hi all,

In my Kubuntu Edgy install, most of my harddrives show up as sdaX, where X obviously is a number. Only my external firewire disk shows up as "Backup" which is it's volume label. How can tell Ubuntu to use the labels of my other harddisks as well, instead of the sda thingy? In Gnome, this was the case by default actually.

Also, when I add the 'storage media' applet to my panel, only Backup (the external drive) shows up. When I select configure applet, it says it is displaying root, sdaX (X = 1,5,6) and backup. I want them to actually show up!

Any ideas?

---

### Post by ComplexNumber on 2006-11-18
i've never tried to change the label, but i think you may have to edit the  label in the /etc/fstab file. before you plunge straight in, wait until you get a few more replies from other people because the fstab is an important file and you could end up wrecking your installation if you do something badly wrong. always back up beforehand.

---

### Post by TheWizzard on 2006-11-18
sdaX? should start with hd. can you post the output of
```
sudo fdisk -l
```
and 
```
cat /etc/fstab
```

normally you are free to choose the mount point for your hard drives. there's no reason to give your harddisks names.

---

### Post by Crakie on 2006-11-19
Doesn't sda mean they are SATA?

Anyway, fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4177    33551721    7  HPFS/NTFS
/dev/sda2            4178        8354    33551752+  83  Linux
/dev/sda3            8355        8877     4200997+  82  Linux swap / Solaris
/dev/sda4            8878       38913   241264170    f  W95 Ext'd (LBA)
/dev/sda5            8878       15405    52436128+   b  W95 FAT32
/dev/sda6           15406       38913   188827978+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

And cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fe93fafa-b08b-4c2d-a3f4-e3c7dccba357 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2B4E0F9B4E0F0B9 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4532-4CBF  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8A64-998A  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=6a4df2f8-f27f-4de2-ac63-0c048d6de7f1     none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Crakie on 2006-11-19
Perhaps it's inappropriate, but... *bump*

---

### Post by nixclusive on 2006-11-19
check out the device labels in: 

```
ls -lh /dev/disks/by-label
```

What do you see?

---

### Post by bodhi.zazen on 2006-11-19
If you want to change the label, it depends on the file system.

See [How to partiton](http://ubuntuforums.org/showthread.php?t=282018) for how to set a label at the time of formatting ; Look near the bottom of the post.

Or change the mount point, which is done via [fstab]() and/or mount.

The fstab thread has a section titled "how to label" which may be of assistance.

---

### Post by Crakie on 2006-11-19
ls -lh /dev/disk/by-label

total 0
lrwxrwxrwx 1 root root 10 2006-11-19 19:09 Backup -> ../../sdb1
lrwxrwxrwx 1 root root 10 2006-11-19 19:09 DATA -> ../../sda5
lrwxrwxrwx 1 root root 10 2006-11-19 19:09 MEDIA -> ../../sda6
lrwxrwxrwx 1 root root 10 2006-11-19 19:09 Windows_XP -> ../../sda1

If I edit my fstab file to use the "Label=..." syntax, should I remove the current entry for sda5 (which uses "UUID=..." as posted above)?

SO, just to be clear, what I want is sda1 to show up as Windows_XP, sda5 as DATA and sda6 as MEDIA. And then I would like the storage media applet in the panel to actually show these devices.

---

### Post by bodhi.zazen on 2006-11-19
Example:

comment out (add a # in the front of) your entry for sda1

Ex:
# /dev/sda1 .....
# UUID=1234 ....

fstab:> LABEL=Windows_XP /media/Windows_XP auto <options> 0 0

Options may include auto,users

Now:```
sudo mkdir /media/Windows_XP
mount /media/Windows_XP
```

You may need to sudo that mount depending on fstab options !

8)

---

### Post by Crakie on 2006-11-19
Thanks, all looks good now :)

---

