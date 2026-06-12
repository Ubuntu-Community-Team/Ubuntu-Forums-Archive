---
title: "How to install Windows XP to a new drive?"
date: 2013-04-13
forum: Any Other OS
---

### Post by ruwan2 on 2013-04-13
Hi,
I want to install Windows XP to a 200 GB hard disk. I have used Gparted to partition the disk to two, the first as 150 MB, I want it for the boot loader for the multiple boot. The second partition is 150 GB, which is for Windows XP. The rest is intend for Ubuntu. No matter I format the first and the second partition to FAT32 or ext2, ext4, Windows XP does not recognize the partition. What is wrong with me? I want to install XP first, then install Ubuntu. Thanks,

---

### Post by Mark Phelps on 2013-04-13
Try doing this with XP as the FIRST partition on the drive.  That should work.

---

### Post by ruwan2 on 2013-04-13
What type should I format the partition? FAT32? Later I still can add Linux partition? I had two OEM computers. One was HP, the other is ASUS. They had Windows XP and Vista installed on the first partition. After I reduce Windows XP and Vista partition, I install Linux. I cannot partition a hard drive like them to get a dual boot PC? Thanks,

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by Sef on 2013-04-13
Moved to Other OS support.

---

### Post by MadmanRB on 2013-04-13
XP is on its deathbed, by next year it will be done for.
Go with windows 7

---

### Post by stalkingwolf on 2013-04-15
My experience is that you have to format the entire drive to either ntfs or fat 32.  Lately fat hasnt been working for me for some reason.  Then install xp then use gparted in a live disk and repartition for your linux partitions.  Windows doesnt read ext partitions and will tell you your drive is bad and not install.

At least that is my experience.And yes as far as I know windows has to be first.

---

