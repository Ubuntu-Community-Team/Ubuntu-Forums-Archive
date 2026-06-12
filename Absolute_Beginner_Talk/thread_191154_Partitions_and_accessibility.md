---
title: "Partitions and accessibility"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-07
Hi, I have already left a thread but maybe it was unclear :mrgreen:  How do I create a partition which I can access from ubuntu? 

Thanks in advance :D  

Mike

---

### Post by Flyn on 2006-06-07
Look around for a program called gparted. It can do pretty much whatever you want when it comes to partitioning. I reccomend that you create a ext3 partition, or a fat32 partition if you want it to be readable from Windows.

---

### Post by MaximB on 2006-06-07
what ?!
ext3 partition is readable and writable from winxp ????

---

### Post by Flyn on 2006-06-07
If you install an installable ext2/3 file system, then yes.

---

### Post by MaximB on 2006-06-07
what do u mean by "install an installable" ?
how do I do it ?
can GPart help with that ?

---

### Post by christhemonkey on 2006-06-07
To install Gparted:
```
sudo apt-get install gparted 
```

From packages.ubuntu.com:
> 
Gparted is a partition editor for GNOME

It is a graphical editor which uses libparted to detect and manipulate devices and partition tables while several (optional) filesystem tools provide support for filesystems not included in libparted. These optional packages will be detected at runtime. It currently supports ext2, ext3, Reiser3, FAT, NTFS, XFS, JFS, HFS and Linux swap.



EDIT: That wasnt what you asked was it...
Gparted wont let you read ext3 in widnows no.

You need to download the windows drivers for reading/writing ext3 from [here]("http://www.fs-driver.org/").

---

### Post by MaximB on 2006-06-07
cool sh*t man !!!
now we need to find other programs that support reiserFS XFS JFS
or even better - somthing that will let you right to NTFS from linux
and is relaible and works (cuz I've found some programs but ppl here say that they aren't good and have bugs).

---

### Post by christhemonkey on 2006-06-07
NTFS write support is in the pipeline.
Currently it is sort of safe, but still not advised as is not 100% there.

---

### Post by rodrigo666 on 2006-06-07
I'm triyng to format one of my NTFS partitions I have to FAT32 through Gparted, but it don't show the option "format" enabled when I right click on it. And when I choose to "unmount" it, it says "could not unmount - device or resource might be in use". But the fact is that it's not! I already has deleted all it has with my Windows XP.

---

