---
title: "accesssing files in windows"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by matawang on 2006-02-06
i have installed breezy in dual-boot mode. wish to spend as much time as possible in linux environment. however, i hv openoffice files in windows drive. how can i access these files as write to the files?
pls help

---

### Post by kingsidy on 2006-02-06
# To mount Windows partition> 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222


to unmount
> sudo umount /media/windows/

hda1 is which ever drive you want to view. usually it is hda1. could be hda2 though if you have two partition in windows and want to view the second.

---

### Post by swguru on 2006-02-06
If your Wondows partition is NTFS, you won't be able to write to it, but you can read it. If you want to be able to share files between Windows and Ubuntu, the partition has to be FAT.

---

### Post by AndyCooll on 2006-02-06
[QUOTE=swguru]If your Wondows partition is NTFS, you won't be able to write to it, but you can read it. If you want to be able to share files between Windows and Ubuntu, the partition has to be FAT.[/QUOTE]

So ...you could create a FAT partition, save all your files to that and then you'll be able to read and write to it whether in Windows or Linux.

:cool:

---

