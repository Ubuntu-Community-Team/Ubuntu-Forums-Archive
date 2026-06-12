---
title: "USB HDD problems :("
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by baz.g on 2007-09-01
Hi,

i decided to format my 80gig USB HDD to ext3 because i will never switch back to microshite again! :D 

i used gparted to format it and it completed successfully, the only trouble is now i have remounted the drive i do not have any permissions to do anything with it. all read/write permissions are given to root only.

there is also a folder on there called "lost+found" that seems to be occupying over 1gig of space.

please help with this, i know this is going to be something really easy but i am still learning this great OS :)

many thanks in advance :)

Baz

---

### Post by EdThaSlayer on 2007-09-01
If you want to change the permissions from root to user, try typing this in the terminal(terminal can be found in applications-accesories-terminal): "sudo nautilus'. Then nautilus will pop up, and have root priveleges. Try right-clicking to find the properties of the HDD and change it to user priveleges. The lost and found folder basically contains lost trash, just delete that folder as you will not need it. If I was you though, I would have formatted the hard drive to fat32, so not only linux, but also windows can mount it(you do have some friends that use Windows right?).

---

