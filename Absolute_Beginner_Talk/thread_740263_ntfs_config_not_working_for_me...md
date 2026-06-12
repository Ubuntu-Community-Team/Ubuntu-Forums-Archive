---
title: "ntfs config not working for me.."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by abhishek613 on 2008-03-30
hi, new to ubuntu, i have ubuntu gutsy installed and after installation 20 gb unalloted space was left.tried to make ntfs parttion but using gparted gave me this..."It is not possible to create more than 4 primary partitions";so i deleted another partition after making a data backup. now i want to combine the original 20 gb and new alloted space from deleting the ntfs partition. however gparted does not support ntfs writing and ntfs- config is not helping!!	:confused: can i get back the partition as ntfs in ubuntu? or should i use vista to do the needful... please help... thanx in advance.:)

---

### Post by lswest on 2008-03-30
Yes, if you install gparted into your ubuntu system you can create NTFS partitions, the only issue would be if you had to resize Ubuntu's partition.

install it with:
```
sudo apt-get install gparted
``` and then run it with ```
gksudo gparted
``` and then have fun! :P

also, as a bit of info for you, You can only have 4 primary partitions on a drive at a time, but you can create an extended partition (basically just groups empty space into a chunk) and create as many sub-partitions as you want.  E.g. my layout on my laptop's drive: Vista: 115GB, Recovery Partition: 10GB, Extended partition: Ubuntu /: 10GB, Ubuntu /home: 15GB, Swap: 1GB.  (you can create an extended partition in GPARTED when creating a new partition just by choosing "partition type: extended" instead of "partition type: primary"

---

### Post by abhishek613 on 2008-04-01
hey thanx for the help, got my partition back! unfortunately had to resort to disk director 10. still not used to gparted, well will learn ubuntu by practice. k bye:)

---

