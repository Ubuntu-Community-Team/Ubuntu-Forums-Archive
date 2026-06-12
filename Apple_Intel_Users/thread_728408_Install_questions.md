---
title: "Install questions"
date: 2008-03-18
forum: Apple Intel Users
---

### Post by egarren on 2008-03-18
I already posted this in the beginner forum, but here it is again.  I have spent hours looking for answers so please help me!! First of all, I have an Apple imac w/ leopard, i partitioned my hardrive to run bootcamp (on 10gb), and I downloaded and burned the ubuntu installer. I don't have parrallels and don't plan on buying it. I also don't have an external hardrive, so I can't back up my 100gb of data. So, I want to install ubuntu on the pc partition of my hardrive without deleting any of my stuff. I have read lots of horror stories about people erasing their entire computer. Can I just select "Manual" on the ubuntu partition screen and then check the box next to the 10gb partition? Thanks!

---

### Post by cyberdork33 on 2008-03-18
you currently should have an EFI partition, the OS X partition, and your bootcamp (FAT32) partition.

Start the Live CD, and run the partition editor. Select the last partition (the FAT32 one) and delete it (yes, that's right).

after you exit the partition editor (which is an app called gparted) start the installer and select to install to the largest free space.

---

