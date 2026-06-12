---
title: "can I ad ubuntu to a dual boot system?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by pmaury on 2006-01-02
how do I install ubuntu on a partition. On a 160gb harddrive, I have a small (2-3)gb fat32 partition, a 40gb ntfs where XP is, 6gb for mepis linux, 1gb for linux swap, and 100gb+ for I think it is where root or home files are, (mostly empty). I have ubuntu on CD from iso I downloaded today.I can't get past the partitioning section.Mepis is debian based with KDE, but I can't figure how to do it with QTParted either

---

### Post by cjm5229 on 2006-01-02
If you have a Mepis CD it should run as a live cd. It will have QTparted on it when you run the install wizard. The first thing you need to do is create a partition. You can find instructions here on how to do that. [http://www.mrbass.org/linux/mepis/installdualboot/]("http://www.mrbass.org/linux/mepis/installdualboot/")
Once you have a partition you can install either Mepis or Ubuntu, with Ubuntu, you just create the partition as free space. then let the Ubuntu partitioner, set up your partitions automatically. Once you have done a few setups if you want to get fancy you can create more partitions for "home" or a fat 32 partition for moving files between Win. and Ubuntu. but keep it simple at first. Here are some pretty good instructions for Dual booting Win and Ubuntu, [http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")
also look in "installation and upgrade help" for more howto's. It seems kind of complicated at first but once you've done it it's really not that hard. Good Luck. Carl

---

### Post by pmaury on 2006-01-02
mepis is already installed on the ext partition,that really is the problem ,do I put ubuntu there or do I create a new partition, if so how?

---

### Post by pmaury on 2006-01-02
GRUB can  select linux or windows at boot . can i make ubuntu one the choices

---

### Post by pmaury on 2006-01-02
useing QTParted the only partition I can't resize or reformat is the 100+gb space at the end with nothing on it .I have already been to dual boot mepis link before,maybe I partitioned it wrong the first time when I installed mepis? the ubuntu disc won't let me install over the mepis

---

### Post by vasudevank on 2006-01-02
if there is nothing on it (meaning in windows it says unallocated (not free space)) then just pop in the ubuntu cd and start the install, ubuntu can take care of partioning free space with just a push of one enter key

---

### Post by Sef on 2006-01-02
> I can't get past the partitioning section.

What problems are you having partitioning?  Could you please describe in more detail exactly what happens.

---

### Post by pmaury on 2006-01-03
I navigate through partitioning disc section choosing every option but the one that erases the whole thing and would leave only ubuntu,when I hit enter I get kicked back to choose again.also the 100+gb space doesn't say 'free' it is called 'unusable'

---

### Post by pmaury on 2006-01-03
XP is only on the 40gb ntfs partition.I want to reformate my unusable space to 'ext2'

---

### Post by Sef on 2006-01-03
>  the ubuntu disc won't let me install over the mepis

You can't install over another Linux system.  You either have to shrink the Mepis partition first or delete the Mepis partition.

---

