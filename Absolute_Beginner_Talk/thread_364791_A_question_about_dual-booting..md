---
title: "A question about dual-booting."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-18
I want to install 6.06 LTS Ubuntu dual-boot with windows xp. I have 74.5gb hard drive(48.9gb used) how big should I make the partition for Ubuntu when I install? Also how easy is it to remove ubuntu, it's partitions and the GRUB boot manager if I decide I don't want it? Also, say my computer gets messed up. Can I use the Live CD(or some other bootable disk) to reformat my hard drive as NTFS and delete the partitions so I can use my hard drive backup software's boot disk to restore my computer? (To before I installed Ubuntu)

---

### Post by bender5788 on 2007-02-18
Installing a dual boot is easy! In regards to on an 80 GB i would recommend the following.
Assuming this is just a test and your not yet comfortable with linux
65 GB for windows (or about 10GB for system and the remainder for files)
2 GB for swap
10 GB for Ubuntu in ext3fs
or at least as close to that as possible
-----------------------------
If your fairly comfortable with linux that should also do the trick but maybe instead of 1 partition of Ubuntu have two one mounted as  / and another as /home


---------------
Oh and as for removing it thats slightly trickier because you will need to somehow refresh the the MBR (Master Boot Record) after you kill the ubuntu partitions
for that i recommend the following
Download a good boot cd and learn to love it.. the one i have has everything from partitioning to password recovery or make  a windows boot disk and then when you get to the recovery console (after deleting the partition type in fixmbr.

---

### Post by Matt1632 on 2007-02-18
Ok.  When I use the Ubuntu graphical installer will it make the swap partition, etc. for me?  I'm really new to linux(Really, I've never used it until this morning) so I don't know how to do the partitioning.  What is the boot cd you use?

---

### Post by bender5788 on 2007-02-19
On the boot cd i use it has partition and MBR tools that is all you need the partition tools will allow you to use erase the drive and the mbr tools will get rid of the linux boot loader
If you need help send me an email or add me on either of the two messenging program i use

---

### Post by saydinli on 2007-02-19
Since you new to Linux (as I am). I would recommend installing a 2nd hard drive and install Ubuntu on that one.  That way there is no threat of ruining your XP install as well as your MBR (as I had done in the past  :rolleyes: 

What I did is install a second HDD and loaded Ubuntu on that drive. I also installed the MBR on that drive as well and set up by BIOS to boot from that drive first. The Ubuntu installer will look for other OS's on the system and add them to the MBR so you will be able to still select to boot XP even though it is not on the same HDD.

This way you don't touch your XP drive at all and risk ruining it or any data on it. If you later decide you don't want to use Linux anymore, you can then just format the drive to NTFS/FAT32 and use it as a data drive for all your files and change you BIOS back to boot from the XP HDD.

---

