---
title: "Permissions"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-08-05
Hello, im sharing a partition with windows, it was formatted using FAT32, i can read the contents on the drive but i cant writte anything unless i do  sudo cp filename hda5 
is there a way to solve this, so that anyone can writte to it?

---

### Post by Jagot on 2006-08-05
You probably need to edit your fstab.  Read this link to mount it properly:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532490](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532490)

---

### Post by poloman2 on 2006-08-05
Thank you!! it worked now... i have another little problem the partiton became writtable but not all it's subfolders, how do i set up all folders to be writeable??

---

### Post by annda on 2006-08-05
this is very strange... the whole drive mounts as writeable, so you should have full access to it.

identify a non-accessible directory and navigate to it using nautilus or terminal, and then do respectively:
--nautilus: right-click and select the permissions tab
or
--terminal: type
```
ls -l
```
the letters on the left (rwx...) tell you what the permissions are.

post the results please.

---

### Post by poloman2 on 2006-08-06
I did open the permissions tab.. 
it says:
Owner  read (checked)   write (not checked)  execute (checked)
Group  read (checked)   write (not checked)  execute (checked)
Others read (checked)   write (not checked)  execute (checked)

text view: dr-xr-xr-x
Number view 555, as far is i know it should be 777...

---

