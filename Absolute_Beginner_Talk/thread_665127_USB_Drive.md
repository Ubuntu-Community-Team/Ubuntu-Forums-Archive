---
title: "USB Drive"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Drezard on 2008-01-11
Total newbie question. I have inserted my USB Drive into my Linux Server system. I'm fairly new to Linux servers and I can not work out how to access the files on my USB Drive. I know its there because Linux can see it when I try a 'fdisk -l' command, but how do I access the files in it?

Daniel

---

### Post by nikoPSK on 2008-01-11
does ```
lsusb
``` show it?

---

### Post by macogw on 2008-01-11
when you do the fdisk -l, what's it listed as?  if you type "mount" does it show there too?  if not, do:
sudo mkdir /media/flashdrive
(so you have a directory where you can mount it)
then 
sudo mount /dev/sdb (or whtever it's listed as) /media/flashdrive
and it should be accessible as /media/flashdrive
then when you're done
sudo umount /dev/sdb (I think...might be to put /media/flashdrive there...if it errors on one, use the other)

---

