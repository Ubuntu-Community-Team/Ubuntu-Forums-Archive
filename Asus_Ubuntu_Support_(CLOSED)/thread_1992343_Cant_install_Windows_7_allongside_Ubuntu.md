---
title: "Cant install Windows 7 allongside Ubuntu"
date: 2012-05-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by diogojg on 2012-05-31
Hi everyone! I've had serious problems installing ubuntu and windows 7 allongside because of the partitions GPT and MBR. I dont understand very well this topic so here i go: I have ubuntu installed using my entire HD, and now i want to install windows 7 allongside with it. The problem is i cant install windows at all. When i choose a partition it keeps saying that the partition is not GPT. 
I cant install windows using my entire drive too. This has been a big probem. On my old computer it was easy to install and remove OS... Is it too dificult to have dual boot on the newer computers?

Thank you!

---

### Post by VE6EFR on 2012-05-31
If I understand correctly, I believe you will need to install windows first and then install Ubuntu. I could be wrong though so perhaps someone with more experience will be able to chime in.

---

### Post by diogojg on 2012-05-31
I cant install windows :/  thats one of the problems. Unless i try to install it using a pen drive. But using a DVD i am no able to install it. Thank you for the reply.

---

### Post by dinutu on 2012-06-01
> **diogojg said:**
> I cant install windows :/  thats one of the problems. Unless i try to install it using a pen drive. But using a DVD i am no able to install it. Thank you for the reply.

Format the entire drive, to be NTFS, make sure it is Master, then choose it to be bootable.
You must definitely install windows first and then any Linux after. Tried many times to do your way but it didn't work. Still if you create a NTFS partition, you will be able to install windows on it, and it goes well, but later you will have to install GRUB to be able to choose between both.. personally never did this way.

---

