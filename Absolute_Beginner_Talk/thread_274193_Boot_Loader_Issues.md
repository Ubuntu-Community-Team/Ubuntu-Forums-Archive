---
title: "Boot Loader Issues"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Straevaras on 2006-10-09
Hi everyone.

My very first shot at trying to dual boot on my laptop with Windows XP and SuSE 10.1 was a terrifying (at times) ordeal.  Eventually I managed to get the problems fixed and I didn't touch anymore from there.  Now I'm trying to dual-boot with Ubuntu and Windows XP (since I love Ubuntu much more than SuSE) and I'm having the same issues as I did the first time.

What happens is that I install Ubuntu on a separate partition like normal, and the master boot record automatically begins to use GRUB for the bootloader from thereon, where I can choose Ubuntu or Windows XP to boot.  Well, randomly (I'm not sure what triggers this) after boot and shutting down windows, something happens to the MBR and suddenly I'm unable to boot from either OS, and GRUB doesn't load anymore! :(   Instead, I get the message:
```
NTLDR is Missing
Press any key to restart...
```
I'm not sure if Windows is randomly modifying the MBR based on something I've done in the OS.  I'm sure that's the case though, that I'm doing something for that to happen, since it doesn't occur every time.  Previously when dual booting with Windows XP and SuSE 10.1, I just decided to use the NT Boot Loader since I didn't have any problems with using that whatsoever (not that I've run into yet either).   So I thought I would do that this time as well.  To set this up, I'm using bootpart, but whenever I set it up with this command:
```
bootpart.exe 3 C:\Ubuntu.lnx "Ubuntu Linux 6.06 - Dupper Drake"
```
and I restart, and it won't boot to that partition (which 3 indicates the third partition on my HD, the Linux Native).  So I decided to try another way and manually set it up by getting the first 512 bytes out of LILO, but Ubuntu (by default) is using GRUB, and I don't know where to go for boot loader options so I can have it use LILO instead!

So can anyone help me with this issue, perhaps explaining why the MBR is being altered, and what I might be doing wrong with bootpart?  I'd rather not have to fool around with the boot loader in Ubuntu, since I particularly like GRUB anyway.  But if push comes to shove, I'll use it. :???: 

Thanks,
-Strae

---

### Post by gn2 on 2006-10-09
> **Straevaras said:**
> Hi everyone.

My very first shot at trying to dual boot on my laptop with Windows XP and SuSE 10.1 was a terrifying (at times) ordeal.  Eventually I managed to get the problems fixed and I didn't touch anymore from there.  Now I'm trying to dual-boot with Ubuntu and Windows XP (since I love Ubuntu much more than SuSE) and I'm having the same issues as I did the first time.

What happens is that I install Ubuntu on a separate partition like normal, and the master boot record automatically begins to use GRUB for the bootloader from thereon, where I can choose Ubuntu or Windows XP to boot.  Well, randomly (I'm not sure what triggers this) after boot and shutting down windows, something happens to the MBR and suddenly I'm unable to boot from either OS, and GRUB doesn't load anymore! :(   Instead, I get the message:
```
NTLDR is Missing
Press any key to restart...
```
I'm not sure if Windows is randomly modifying the MBR based on something I've done in the OS.  I'm sure that's the case though, that I'm doing something for that to happen, since it doesn't occur every time.  Previously when dual booting with Windows XP and SuSE 10.1, I just decided to use the NT Boot Loader since I didn't have any problems with using that whatsoever (not that I've run into yet either).   So I thought I would do that this time as well.  To set this up, I'm using bootpart, but whenever I set it up with this command:
```
bootpart.exe 3 C:\Ubuntu.lnx "Ubuntu Linux 6.06 - Dupper Drake"
```
and I restart, and it won't boot to that partition (which 3 indicates the third partition on my HD, the Linux Native).  So I decided to try another way and manually set it up by getting the first 512 bytes out of LILO, but Ubuntu (by default) is using GRUB, and I don't know where to go for boot loader options so I can have it use LILO instead!

So can anyone help me with this issue, perhaps explaining why the MBR is being altered, and what I might be doing wrong with bootpart?  I'd rather not have to fool around with the boot loader in Ubuntu, since I particularly like GRUB anyway.  But if push comes to shove, I'll use it. :???: 

Thanks,
-Strae

Dupper=Typo? Shouldn't it be Dapper?

Dual booting best done with dual hard drives....

You can have Ubuntu on a USB drive.

---

### Post by Straevaras on 2006-10-09
I know it would best be done with two hard drives, and I know I can boot from a USB drive, but I'm working on a laptop.  I won't always be carrying around a USB drive with me and I only have one hard drive in my laptop. :???:

And yes, that is a typo, it should be Dapper.

By the way, when trying to use bootpart and boot off of that, I get this when trying to boot:
```
BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant http://www.winimage.com/bo
otpart.htm
Loading new partition
Bootsector from C.H. Hochstätter
Cannot load from harddisk.
Insert Systemdisk and press any key.
```

---

### Post by Straevaras on 2006-10-09
I'm still not having any luck.  Would anyone happen to know why Windows might be altering the MBR?  It's something I'm doing and I don't realize it.

---

### Post by bulldog on 2006-10-09
Well I shouldn't know what to do to have windows alter the MBR without the cd.

You can install GRUB again however,using the live cd.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by Straevaras on 2006-10-09
Oh, that's a wonderful alternative to what I had in mind.  Thanks a bunch! :D :D :D

Also, do you think using PartitionMagic would have something to do with Windows modifying the MBR?  That's the only thing I can think of.

---

### Post by bulldog on 2006-10-09
> **Straevaras said:**
> Oh, that's a wonderful alternative to what I had in mind.  Thanks a bunch! :D :D :D

Also, do you think using PartitionMagic would have something to do with Windows modifying the MBR?  That's the only thing I can think of.

That's possible but on the other hand I really don't know how.

You should have giving the command to alter the MBR.

---

