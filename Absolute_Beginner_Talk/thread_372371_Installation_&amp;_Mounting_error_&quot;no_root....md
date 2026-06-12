---
title: "Installation &amp; Mounting error &quot;no root...etc&quot;"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ranker on 2007-02-28
Hi everyone,

I'm a newcomer to the Linux OS.  I've been trying to setup a triple boot on my dell intel laptop.  I've already got Vista installed.  I used Gparted Live CD to setup 4 partitions for my 100 gig HD.  

My first partition is NTFS (50 gigs) for my Vista installation = partition 1

I created an EXT2 (20 gigs) for Ubuntu = partition 2, linux-swap (4 gigs) as the linux swap partition, and FAT32 (20 gigs) for OSX86 = partition 3.  

I boot up the 6.10 ubuntu CD as normal and get all the way until the partition/mounting section (I think its part 5 of 6 of the install routine). 

I see 4 things show up on the right hand column pertaining to my 4 partitions.  On colums, I set "blank" for partition 1 (my Vista partition), I set "/" for my partition 2 (where I'd like Ubuntu to go), I set "linux-swap" for partition 3, and I set blank for my partition 4 (where I will later install Jas OSX 10.4.8.

However, whenever I click next I get the error sign "no root file system".  I'm not sure what i'm doing wrong as I made sure I was following the instructions and making sure I'd set at least one partition to "/" for root.  

I've been following the guide here: [http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html](http://cybernet1.blogspot.com/2006/10/how-to-triple-boot-windows-mac-os-x.html) to setup a triple OS boot on my laptop for those wondering. 

Any help or pointers would be appreciated!

Thanks in advance,

Karl

---

### Post by Kateikyoushi on 2007-02-28
I would try to make a new ext3 for ubuntu. Delete it reboot and make new partition and tick the format checkboxes.

---

