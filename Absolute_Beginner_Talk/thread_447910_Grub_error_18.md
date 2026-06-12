---
title: "Grub error 18"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by jerf on 2007-05-18
so my roomate says he opened up amule one day, the windows began flashing/switching back and forth so he shut the computer down.  shutdown went fine (apparently).  

now after the POST grub tells me to please wait...but is unable to load with error 18.

ive read that its related to hard drive settings and the size of the mbr but im not clear how to resolve the issue, especially when the bios and a failed grub load, or boot, whichever it is..are all i have to work with on that comp.

thnks

---

### Post by theicyj on 2007-05-18
This happened to me once with OpenSuse dual-booting with Windows Vista a while ago, both installed on a sata drive.  I fixed it temporarily by removing my IDE drives, not an ideal fix.  Since then I have used Ubuntu Feisty and Vista in dual-booting conf with no ide drives and no problems.  Sorry, that is probably not to helpful.

There is a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/9006]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/9006")

---

