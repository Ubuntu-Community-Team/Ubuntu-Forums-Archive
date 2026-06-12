---
title: "I Need Help Uninstalling Ubuntu 7.04"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by vinnard on 2007-05-29
Hi, I recently installed ubuntu linux 7.04 desktop edition on my computer. I now want to uninstall it. The last time I just reformatted the harddrive partition it was on and the computer wouldn't boot at all, so I reinstalled it and now I don't know what hard drive I put it in, and when I try and log on to my ubuntu account, to check, it will not let me log on. Any help would be greatly appreciated!
Thanks in advance, Vinnie

---

### Post by mocqueanh on 2007-05-29
Because hard disk has a personal partition, called Master Boot Record, it contains all informations about your OS to start up

check here:
```
http://ubuntuforums.org/showthread.php?t=454542&highlight=uninstall+Ubuntu
```

Or the easiest way is: for mat your Ubuntu partition and swap partition to FAT32, or NTFS (file system of Windows )
Reinstall Windows, and it will overwrite the MBR ( assume you have 2 or more partition of Win, one partition for install Windows and programs on Windows, one partition you contain you important data, such as: music, movie, setup file of softwre.......)

---

