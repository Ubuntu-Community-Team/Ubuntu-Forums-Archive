---
title: "External Hard Drive problems"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Fos23 on 2007-12-20
Hello everyone I just bought an Seagate external formated to NTFS. I used pmount to mount it, but i don't have permissions to write to it. I tried to change the permissions, but i get an error message telling me that this is a read only disk. Any way to fix this? I tried to reformat it to ext3 using Gparted, but i still couldn't write to it.

---

### Post by Fos23 on 2007-12-20
oh, one more thing, I have had no trouble at all with my WD Passport formatted to Fat32

---

### Post by Fos23 on 2007-12-21
Well, I got it to work, I'm not quite sure how, but this is what i did: downloaded ntfsconfig, checked the box for external hard drive write support, but that still didn't work. Then I upgraded to Gutsy (was running Feisty), and now it works. :D

---

