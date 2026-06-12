---
title: "image drive on ubuntu??"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by MeRcYFuL_FaTe on 2006-09-11
hey guys,
does anybody knows a program to mount *.iso/*.nrg files as nero's image drive program or daemon tools?

---

### Post by haxer on 2006-09-11
Try this


sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom





sudo umount /media/cdrom

---

