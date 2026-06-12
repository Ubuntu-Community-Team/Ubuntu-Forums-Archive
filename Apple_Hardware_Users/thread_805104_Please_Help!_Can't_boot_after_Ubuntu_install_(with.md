---
title: "Please Help! Can't boot after Ubuntu install (with GRUB installed on hd0 of a GPT hd"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by milstein on 2008-05-23
Hi all,

I had a working OSX86 installation (using Kalyway 10.5.1 DVD + update) on my Thinkpad hard drive
Before Ubuntu installation, the hard drive was partitioned using GPT (Guid Partition Table, not MBR):
- OSX 70 gb
- DATA 125 gb
- LEODVD 5 gb
It booted directly into the OSX partition (in darwin bootloader)

1. First of all, I tried installing rEFIt onto my hard drive (rEFIt - An EFI Boot Menu and Toolkit [http://refit.sourceforge.net/](http://refit.sourceforge.net/)), which is actually designed for MacBook to multiboot without bootcamp. However, I suppose it did not work as I cannot see any load menu after boot (But I did not have more than one OS at that point)

2. Then, I shrunk the OSX (/dev/disk1s1) using diskutil and freed 20gb after the OSX partition for the Ubuntu installation

3. In the Ubuntu 8.04 installation, I created a 18gb ext3 partition and then a 2gb swap partition. And then I installed Ubuntu onto the ext3 partition

4. At the end of the installation, I have GRUB (the linux bootloader from Ubuntu's disk) installed onto the hd0 (oops... for the whole disk... instead of just for the partition)
In the boot afterwards, I can only see 1 short line of random codes, and it halts there

5. In WinXP (I can see GPT partitions in my WinXP using "GPT Mounter"), I can now only see the DATA and LEODVD partitions, but I can no longer see the OSX partition

I assume that GRUB has done something to corrupt my GPT (Guid partition table)
Is there anyway to restore it?
I really need your help!!!

(I understand that I am not a genuine Apple hardware user in this case, but I do work on a few Mac Pro in daily basis. And I think restoration and rescue procedure for MacBook/MBP will be similar to that on a OSX86 laptop. Thanks in advance!)

---

