---
title: "Mounting Problems"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by eternalis on 2006-09-05
Hi everyone.

Well, I was experimenting with mounting partitions and changing mounting points. So I changed two of my FAT32 hard drive's mounting points from /media/hda5 & /media/hda6 to /FAT1 and /FAT2 by editing the /etc/fstab file. Everything went well, and two new icons : /FAT1 and /FAT2 appared on my dekstop. But, after I rebooted, these icons disappeared and the two partitions (FAT1 and FAT2) aren't shown inthe file browser (in the left-hand Places Panel). But they are mounted as I can access them from the command line or by clicking on the mounting points in the File Browser.

Does anyone know whats wrong here and how I can fix it?

Thanks,

---

### Post by orb9220 on 2006-09-05
Look in /media folder and see if folders fat1 and fat2 if not create folders named fat1 and fat2 and reboot.

If you still have problems then post your fstab here.

---

### Post by eternalis on 2006-09-05
OK, I think I know what I was doing wrong. Before I just created a mount point in my home/user directory, do I have to create it in my /media/ directory?

So, I created the new folders, and edited the fstab file, but nothing showed up on my desktop. I even tried the Ctrl+Alt+Backspace Reboot. Do I have to reboot my computer for everything to show up?

Here is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0      $/dev/hda5       /media/FAT1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda6       /media/FAT2     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Thanks for the help.

---

