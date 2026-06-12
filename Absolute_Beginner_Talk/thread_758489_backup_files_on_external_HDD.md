---
title: "backup files on external HDD"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by freerid3 on 2008-04-18
Hi! I have a bunch of music, movies and pictures on my computer. I want to install Kubuntu on my computer, currently running WVista. Now: If I were to save all my files on an external harddrive, then kill windows installing Ubuntu would I be able to safely and without any problems read these files in Ubuntu? 

Thanks

---

### Post by joshrobinson on 2008-04-18
you can use NTFS in ubuntu, also fat32
fat32 is easier and safer for linux to read and write to, but you cant have files over 4gb on a fat32 partition

either way would work though

---

### Post by bumanie on 2008-04-18
If you format the external drive to ext3, no problem. If you format it to ntfs, there should not be any problem as long as you install ntfs-3g and ntfs-3g config. This will give you an option in Applications --> System tools to enable read/write to an external ntfs devices. You could also use FAT32 on the external device as linux natively can read/write to FAT32. If your movies are large, go for ntfs. You will find, after getting some experience, that linux is quite flexible.

---

### Post by Mick8882003 on 2008-04-18
you may have trouble with the usb part, ive had all sorts of trouble getting usb hard disks to work.

---

