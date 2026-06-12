---
title: "Format of the partitions"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by StephUb on 2007-08-16
Hello there,

I checked the stickies and couldn't find all the informations...
I wanna keep my W and have dual boot on my laptop with ubuntu.
I understood i am gonna have to keep W on NTFS, create an ext3 for Ubuntu install, create a document partition shared between the two OS in FAT32 (may I keep it in NTFS ???) and create a SWAP disk...

What format should i use for the swap partition ? i was thinking a ext3 because that's the virtual memory for ubuntu, but i am not that sure...


Thanks a lot

---

### Post by misconfiguration on 2007-08-16
SWAP uses SWAP if you're using fdisk it's type 82.

If you're using this with a GUI setup, once you select the partition to be SWAP it generally does everything automagically.

You shouldn't need to do anything extra. REMEMBER SWAP should be twice your RAM size, some recommend it never to go over 2gb.

---

### Post by jnorthr on 2007-08-16
don't think you really have a choice for the swap file but ext3 is fine. be sure to make it 2 or 3 times your ram size. Put the swap partition first after the fat32 partition for w. on my kit i put /home in the next partition so i can keep all my config. choices, mail address settings, etc, then a /usr/local partition to preserve all my editors like eclipse and java compilers, finally a root partition for the rest of the disk. Note you can only have 4 primary partitions, so if you choose to make more than 4 partitions, you will need the first three partitions to be primary partitions and the fourth becomes an 'extended' partition that is really just a pointer to any further partitions you choose to make.

---

### Post by Bachstelze on 2007-08-16
The swap has it's own filesystem, actually it doesn't have one :p

---

### Post by StephUb on 2007-08-16
Ok thanks a lot,

I am gonna install unbuntu on my laptop (or try to install it at least) as soon as i get it back..

So as far for the partition,
Part1: FAT/NTFS : Win
Part2 : SWAP
Part3 : Ext3 : Ubuntu
Part4 : FAT : Files

Am i right ??

Again, thanks
I feel like a newbie in linux but i am fed up with Win....

---

### Post by StephUb on 2007-08-17
Hummm..

I have another question about dual boot...
Where do i put the Grub because i would like to keep windows boot loading (well i prefer to keep the MBR on my laptop clean because it might be tatooed)

Thanks

---

