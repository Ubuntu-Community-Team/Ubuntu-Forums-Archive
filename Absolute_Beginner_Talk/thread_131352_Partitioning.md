---
title: "Partitioning"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by lzfy on 2006-02-16
Hi, i'm gonna remove all my partitions and setup an multiboot environment with Windows XP and Ubuntu. This is how it will look like:

15 GB Windows partition
14 GB Ubuntu
1 GB Swap
the rest is for NTFS Data

My question is how should i do this, i mean should i create the linux partitions after the Windows partition or after the NTFS Data partition.
something like this?

Windows - Ubuntu - Swap - NTFS Data

or

Windows - NTFS Data - Ubuntu - Swap

please help. thanks :)

---

### Post by frodon on 2006-02-16
You can do it in the order you want but always install ubuntu after windows when you have the choice and keep in mind that you will **NOT** have write access on NTFS partitions under linux.

---

### Post by Arktis on 2006-02-16
Set up your windows installation first, then install ubuntu.  Otherwise, windows will mess up grub.  You can set up your extra data partition whenever you like; it won't matter.  By the way, have you considered making a small root partition and using the rest for a separate home partition?  4 gigs will be more than enough for root, leaving it plenty of room to grow if needed.  Root only uses about 2.2 gigs anyways.  Your partition table would look something like this:

Windows - 15
/ - 4
/home - 10
swap - 1

---

### Post by ssalman on 2006-02-16
I would add that if you expect to resize your NTFS data partition in the future, put it last, it would save some troubles

---

### Post by lzfy on 2006-02-16
[QUOTE=frodon]keep in mind that you will **NOT** have write access on NTFS partitions under linux.[/QUOTE]

I know that :) 

> Set up your windows installation first, then install ubuntu. Otherwise, windows will mess up grub. By the way, have you considered making a small root partition and using the rest for a separate home partition? 4 gigs will be more than enough for root, leaving it plenty of room to grow if needed. Root only uses about 2.2 gigs anyways. Your partition table would look something like this:

Windows - 15
/ - 4
/home - 10
swap - 1

I was thinking of that but woulnd't i have then too many partitions? or isn't that a big deal.

So i this an good order?

Windows (Primary) - NTFS Data (Logical) - Ubuntu Root (Primary) - /Home (Logical - Swap

---

