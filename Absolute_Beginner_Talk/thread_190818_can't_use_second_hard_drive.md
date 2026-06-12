---
title: "can't use second hard drive"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Mbuhrow on 2006-06-06
Hi,
I have a slave hard drive that was format with windows. I've already went through getting it to mount at startup, and I have no problem viewing stuff on the disk, but I cannot write to it. I have it mounted on /media/hdb1 should I mount it somewhere else? I've even tried to change its permissions but I can't do it even with sudo. Any help would be greatly appreciated, as I've already been through the forum and wiki and nothing I read helped me

---

### Post by aktiwers on 2006-06-06
Is it NTFS partition or FAT32? Linux can not write to NTFS. Only Fat32.

To find out if you dont know what filesystem it is, go to the Start Menu=>Systems=>Administration=>Disks

Look at your disk at read what filesystem it is. NTFS or FAT32.

---

### Post by Mbuhrow on 2006-06-06
hmmm... windows virtual fat.
windows reports it as just FAT

---

### Post by aysiu on 2006-06-06
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Mbuhrow on 2006-06-06
first of all fdisk reports it as fat16.
second of all no luck with that link.

---

### Post by Mbuhrow on 2006-06-06
ok, I just realized I should mention that this hd is rather old and only 1.5gb, is that why windows formats it fat16?

also I tried mounting my windows partion which is fat32 and I can read but can't write to that either.

---

### Post by aktiwers on 2006-06-06
Yes thats why its FAT16. You should be able to read and write to both of them.
Follow the guide Aysiu posted.

---

### Post by Mbuhrow on 2006-06-07
OK, I got it, but I don't really know why the guide didn't work for me the first time.

oh well.

thanks guys for helping and thanks to everyone involved with this awesome forum. without it I would still be using winME, ughhh.....

---

