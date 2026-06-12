---
title: "USB Flash Drive"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by bobgb4 on 2006-03-31
I have a Kingston Data Traveler (128MB)...

I have Windows running on one harddrive while Ubuntu on another.  After mounting both windows and usb, I started copying some files.  Suddenly, I started getting the message "There is no space on the destination..."  I tried it in both the file manager and the terminal-same problem.

I look into the properties of the drive and it shows: 
Contents: 60.3MB
Volume: 120.2

Tried rebooting, deleting some files, but nothing seems to work.

Any Help???
Thanks.

---

### Post by professor_chaos on 2006-03-31
Maybe check the drive with fdisk or gparted to make sure you only have the one partition. If it wasn't for your drives properties showing so much space free, I would say check the .Trash folder or something like that. 
Can you remove a file from the drive and put it back on?

---

### Post by bobgb4 on 2006-03-31
thx, it was the trash...

I don't know how I missed it

---

