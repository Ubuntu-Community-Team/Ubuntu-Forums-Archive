---
title: "still can't write to vfat"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by wd3thatsme on 2006-03-17
i mounted and remounted, i edited my fstab, still can't write to vfat, it boots up ok and on desktop but can't write to it...here's my fdisk and etc..... help

Disk /dev/hda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        2432     9767520   83  Linux
/dev/hda3            3633        3739      859477+   5  Extended
/dev/hda5            3633        3739      859446   82  Linux swap / Solaris

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2433    19543041    c  W95 FAT32 (LBA)



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /media/windowsD vfat    iocharset=utf8,umask=000  0 0

---

### Post by aysiu on 2006-03-17
The only thing I can think of is the fact that the /media folder has special functionality (for example, for automount applications like ivman or gnome-volume-manager) directories are often created in there on-the-fly.

You could try mounting it to a static directory instead: ```
sudo umount /dev/hdc1
sudo mdkir /windows_d
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then change ```
/dev/hdc1 /media/windowsD vfat iocharset=utf8,umask=000 0 0
``` to ```
/dev/hdc1 /windows_d vfat iocharset=utf8,umask=000 0 0
``` save (control-x), confirm (y), and exit (Enter). Then ```
sudo mount -a
```

---

### Post by wd3thatsme on 2006-03-17
that seemed to help. i noticed the hd icon is off the desktop is that normal? i can go to the folder and choose files and even write to hd. what do i do with the othe media/windowsd folder, it's empty now? i would like to put u in my buddy list may i?
\\:D/

---

### Post by aysiu on 2006-03-17
[QUOTE=wd3thatsme]that seemed to help. i noticed the hd icon is off the desktop is that normal?[/quote] Sure, since it's not mounted in /media any more. If you want, you can middle-click-drag the /windows_d folder to the desktop and select "link here." 

> i can go to the folder and choose files and even write to hd. Great! 

> what do i do with the othe media/windowsd folder, it's empty now? You can just leave it. Or, you can delete it: ```
sudo rm /media/windowsD
``` 

> i would like to put u in my buddy list may i?
\\:D/ What does that entail exactly?

---

### Post by wd3thatsme on 2006-03-18
i did "sudo rm /media/windowsD" and this is what i got:

 rm: cannot remove `/media/windowsD': Is a directory

as far as the buddy list thing, i just wanted the comfort of knowing i can call a real expert for help, nothing else, no offense.

---

### Post by Sutekh on 2006-03-18
Try
```
sudo rmdir /media/windowsD
```

---

### Post by wd3thatsme on 2006-03-18
it worked yeah, thanks thanks thanks!  i have another problem now. I read my email with thunderbird and wanted to save the email, now i'm getting this message....

"unable to save the message. Please check your file name and try again later."

that means i can't save to the hd right?  wait a minute.. i just saved a mp3 to the windows_d hd so i can save files, why not thunderbird?

---

