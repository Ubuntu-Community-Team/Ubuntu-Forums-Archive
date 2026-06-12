---
title: "external hard disk read only"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Roger D on 2007-12-05
Hi
My external hard disk - a Western Digital My Book, has suddenly become read only. Any ideas? Could the disk just have failed, and how could I test for this condition?

Roger D

---

### Post by bartoni on 2007-12-05
is it FAT32?

---

### Post by Roger D on 2007-12-05
Yes, I think so, but not absolutely sure

---

### Post by bartoni on 2007-12-05
The only reason I ask is that I remember being unable to write on NTFS drives a year or so ago.  This might be supported now though.

---

### Post by Roger D on 2007-12-05
It used to work

---

### Post by koleoptero on 2007-12-05
My external HD is a WD My Book too. I have converted it to ntfs but I have no problems since ntfs-3g is installed by default in gutsy. You should try to install that tool that lets you configure what you want to be read-only and what not. Open synaptic package manager and search for ntfs-config, and play with it's settings.

If you don't want to do that you can try using a different USB slot (if the drive is usb).

---

