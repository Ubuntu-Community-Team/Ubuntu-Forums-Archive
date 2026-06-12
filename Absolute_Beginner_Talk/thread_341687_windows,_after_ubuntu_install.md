---
title: "windows, after ubuntu install"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Wonslung on 2007-01-19
hello, i'm not totally sure if this is the right place for this but i'm guessing more people here will have an answer for this issue than in another forum

i installed ubuntu on a second hard drive my first hard drive looks like this mbr has GRUB then first partiton is windows, second partiton is program files for windows and other 3rd party programs  then the next hard drive first partiton is Ubuntu, second partion is a fat32 drive i designated /share then another fat32 designated /share2 and finally the linux swap file

The problem is that windows isn't recognizing my 2 share drives..what do i do
i'm hoping i don't have to reinstall everything but i'm wondering if it's because the first part of the second hard drive isn't a primary partition that windows can read...thanks for any help

---

### Post by Wonslung on 2007-01-19
nevermind, i figured this out, for anyone having the same problem i did this

put in my ubuntu live cd, went to the partitioner

found my fat32 drives right clicked and went to flags checked lba

restarted, windows recognized them, restarted again and formated them in the windows command shell (only because they were still showing folders from previous software) 
make sure to put the /fs:fat32 behind the format:(drive letter) like so 

format F: /fs:fat32

---

### Post by Sef on 2007-01-19
Thank you for posting your solution to your problem, so that others may benefit from your experience.

---

