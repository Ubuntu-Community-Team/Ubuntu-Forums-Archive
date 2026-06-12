---
title: "Ubuntu on Mac Mini?"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by Narshwal on 2008-06-12
(I'm re-posting here from Hardware and Laptops.)

I am very seriously considering purchasing a Mac Mini with the highest-performing optional hardware configurations, such as 2GB of memory and a 160GB hard drive. With it, I plan to dual-boot Mac and Ubuntu.

What I'd like to know is if there are any incompatibilities with the Mac Mini. I'm also interested to know how well it handles Desktop Effects.  If anyone could help out, it would be greatly appreciated.

P.S. On a sidenote, if I did go with this, I think I'd create one partition for ALL media (including documents) that could be shared by Mac and Ubuntu. Could someone give any ideas on a suggested setup for all the partitions and sizes for them (one Mac, one Ubuntu, one media, and one swap)? Really, thank you thank you thank you ahead of time!

---

### Post by Narshwal on 2008-06-12
Hello? I'm aware of the other Mac Mini threads but they don't give me what I'm looking for, please help out!

---

### Post by adewale on 2008-06-12
Well you'd probably have reasons for wanting a mac , so simply go to a store and run a live cd and if its good for you fine .

---

### Post by cyberdork33 on 2008-06-12
> **Narshwal said:**
> (I'm re-posting here from Hardware and Laptops.)you should not repost, but instead request that your thread be moved using the "report" button.

> **Narshwal said:**
> I am very seriously considering purchasing a Mac Mini with the highest-performing optional hardware configurations, such as 2GB of memory and a 160GB hard drive. With it, I plan to dual-boot Mac and Ubuntu.

What I'd like to know is if there are any incompatibilities with the Mac Mini. I'm also interested to know how well it handles Desktop Effects.  If anyone could help out, it would be greatly appreciated.
There are several threads about the Mac Mini both here and in the Archived forum. All in all, the mini works pretty well. I think your biggest issue will be WiFi (and I am not sure which chipset they have in them now otherwise I would point you in the right direction). Desktop effects should work as the Mini has the same graphics as the MacBooks.

> **Narshwal said:**
> P.S. On a sidenote, if I did go with this, I think I'd create one partition for ALL media (including documents) that could be shared by Mac and Ubuntu. Could someone give any ideas on a suggested setup for all the partitions and sizes for them (one Mac, one Ubuntu, one media, and one swap)? Really, thank you thank you thank you ahead of time!You can do Home partition sharing but that is not recommended. If you really want to, search the forum archive as several people posted about doing that.

What I would recommend is a FAT32 shared partition that you can be shared very easily between OS X and Ubuntu. 

The specific partition sizes are really up to you, and probably more dependant on what you plan to so in each OS. My recommended Install procedure would be to Use Bootcamp to resize your OSX partition and create a FAT32 partition that is size of the space you want for all the other partitions (Ubuntu, swap, storage). After that, boot into the Ubuntu Live CD and start gParted (Partition Editor). Use gparted to resize your FAT32 partition to the size you want and then create your Ubuntu partition, and a swap partition that is at least the size of your RAM. (You can do without the swap, but it is still recommended practice). You layout would look something like:

[LIST=1]
[*]EFI Partition - This is already there and part of the EFI system on your Mac
[*]OS X Partititon - This is already there
[*]Shared FAT32 Partition
[*]Ubuntu Root Partition
[*]Swap
[/LIST]

---

### Post by BlissBryan on 2008-06-12
I have tried the LiveCD on my MacMini, and things seem to work pretty well. I haven't tried the wireless though, so I can't comment on that. 

One thing I noticed is that Ubuntu can read my Mac OS Extended filesystem on my external hard drive. So for a shared data partition between MacOS and Ubuntu, you can use the Mac filesystem rather than FAT32. (well, perhaps first check to see if writing to the Mac filesystem is well supported, as I didn't do this).

So my experience here is limited, as I have only booted up the liveCD and tried the apps on ubuntu. Internet worked fine, and I was able to watch my downloaded movies.

---

### Post by cyberdork33 on 2008-06-12
> **BlissBryan said:**
> One thing I noticed is that Ubuntu can read my Mac OS Extended filesystem on my external hard drive. So for a shared data partition between MacOS and Ubuntu, you can use the Mac filesystem rather than FAT32. (well, perhaps first check to see if writing to the Mac filesystem is well supported, as I didn't do this).
There is limited support for HFS+ in linux, but it is not reliable. Plus, in order to make the filesystem writable, you have to disable journaling which makes your data vulnerable to corruption.

i.e. stick with FAT32 (or even NTFS)

---

