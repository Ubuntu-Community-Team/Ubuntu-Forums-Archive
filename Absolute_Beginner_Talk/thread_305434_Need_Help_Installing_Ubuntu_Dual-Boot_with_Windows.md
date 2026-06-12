---
title: "Need Help: Installing Ubuntu Dual-Boot with Windows, Use NTLDR"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2006-11-23
Hi, I know this will seem incredibly noobish, and it probably already has been discussed a thousand times before, but I need help configuring Ubuntu to install but keep the Windows XP NTLDR for rolling back and convenience. I have a 40 GiG harddrive, and have resized the XP (NTFS) partition (it took up everything) down to 20 Gigs (and it works, I am posting from Firefox XP).  I have also created a 6.5 Gb Neutral FAT32 partiton for sharing.  I have also created a 761 MB swap partition (in GParted) and a 10.02 GB ext3 partition for Ubuntu.

I've put a copy of NTLDR and boot.ini on my FAT32 partition for safe keeping.

I've gone through the Ubuntu installer all the way to the 'install' button, I just need to know how to go about this.  Where would I install GRUB?  How do I bridge the partition gap to start Ubuntu through NTLDR?  How do I keep the XP partition unaffected, and still the boot master?  These questions plague me, and I fear I will not install Ubuntu until I am assured it is safe.

---

### Post by Sef on 2006-12-04
> How do I bridge the partition gap to start Ubuntu through NTLDR?

You can't do it through NTLDR.  Windows only boots Windows.  GRUB will boot Linux and Windows.

> How do I keep the XP partition unaffected, and still the boot master?

You would have to go into [GRUB]("http://ubuntuforums.org/showthread.php?t=311897&highlight=Windows+default") and set XP to be the default operating system.

---

### Post by StriperTS on 2006-12-04
There are two ways that I have used NTLDR to dual-boot Windows XP and Linux.

If you do a Google search for "howto NTLDR install grub" you will find them.  The first way is a little involved and requires you to copy the first section of your Linux hard-drive into a binary file and copy that to your Windows partition, etc.. it works, but every time you modify the Linux bootloader it requires you to take another snapshot into a binary file and copy over to Windows partition.

The other method uses a small program called Grub4Dos, and is what I am currently using to dual-boot XP/Kubuntu.  With this option, you simply add a line to your boot.ini file which adds an NTLDR boot menu option that calls Grub4dos.  Grub4dos loads a menu.lst file which has the same format as the standard Grub file and performs the same function.

Hopefully this info gets you pointed in the right direction.

-- Tom

---

