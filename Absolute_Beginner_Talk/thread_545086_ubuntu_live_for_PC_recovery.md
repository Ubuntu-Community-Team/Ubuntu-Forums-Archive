---
title: "ubuntu live for PC recovery"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by adwatkin19 on 2007-09-07
This weekend i am going to repair a friends computer, but they first need some files recovered from an old ntfs partition that will no longer boot. 

I want to use ubuntu live cd to get the information off the drive and onto a memory stick, there isnt much of it. 

so my questions are:

1. does the live cd have the ability to mount an ntfs drive even just read only so i can copy the files

2. if not could i put the ntfs-36 files on a memory stick and then install them in the live version and then mount the ntfs drive

3. will the live version be able to actually mount my usb memory stick?

many thanks for any help that anyone can give, i really appreciate how great you guys are.

adwatkin19

---

### Post by aJayRoo on 2007-09-07
Yes the live version can mount your ntfs partition, I had to use it for taking files from a broken windows install just yesterday! You shouldn't even have to type any commands just got to computer in the places menu and double click on the ntfs partition and it should automatically be mounted. As for the usb drive that should work fine too! Hope it all goes well.

---

### Post by hyper_ch on 2007-09-07
but it cannot write to ntfs by default... so if your memory stick is ntfs you need to install additional drivers.

---

### Post by BrendanM on 2007-09-07
Most usb keys are FAT32. You can also install ntfs write support from within the live CD, if necessary.

---

### Post by hyper_ch on 2007-09-07
Exactely... most are... not all ;)

Mine has some ext3 partition and a fat32 one ;)

---

