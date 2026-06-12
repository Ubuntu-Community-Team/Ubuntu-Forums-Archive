---
title: "problems setting up dual boot"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Ryokukitsune on 2007-04-14
Well here is my situation,

I have an existing install of windows on my primary hard drive. I’m trying to install ANY incarnation of Ubuntu on a secondary drive though I’ve found out that my system configuration is contributing to the dilemma of the install

My primary drive is SATA and the secondary drive I’m installing to is PATA (IDE)

Where I want to use Linux a lot I am still more comfortable working under windows (small steps rite =P ) so I want to use the Windows Boot loader to load each OS. Unfortunately that’s proving to be problematic.

I’ve tried to use the “dd” command under Ubuntu to generate the volume boot record for Linux (local on disc not from liveCD) but it throws out errors or the file doesn’t work. ( “size=512” portion of the string isn’t accepted, I can get the string to work by changing it to “bs=512”. Though it didn’t produce desired result) 

I’ve also tried to generate the same file under windows with BootPart.exe it generates a file but it doesn’t work. After setting up the boot.ini and rebooting it asks for a system disk. 

After running bootpart it has found the fallowing drives and returned this:

```
C:\>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant
WEB : http://www.winimage.com and http://www.winimage.com/bo
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : bce1bce1
 0 : C:* type=83  (Linux native), size= 74951226 KB, Lba Pos
 1 : C:  type=5  (Extended), size= 3196935 KB, Lba Pos=14990
 2 : C:  type=82   (Linux swap), size= 3196903 KB, Lba Pos=1
Physical number of disk 1 : 8d0a8d0a
 3 : D:* type=7  (HPFS/NTFS), size= 117218241 KB, Lba Pos=63
Physical number of disk 2 : ed613c1e
 4 : E:  type=7  (HPFS/NTFS), size= 488384001 KB, Lba Pos=63
Physical number of disk 3 : 7f3dbcda
 5 : F:* type=b  (Win95 Fat32), size= 985072 KB, Lba Pos=32
```

I can’t open and read the files generated to redirect the boot process so I can’t check the validation of the files and restarting over and over is getting really old.

The only way I can get Ubuntu to boot is to insert the LiveCD and select the boot from first hard drive option. After that Grub loads (I’ll be damned if I can find it in the filesystem) hopefully someone with a little more experience on the subject of dual booting can help me with this problem.

That’s about the whole story

Thanks to anyone who responds,

Ryoku

---

### Post by thefoolisme on 2007-04-14
My guess is that the Windows Boot loader doesn't want to place nice with Ubuntu.  It probably thinks, "You have Windows, why would you want to access anything else?"  :-)  I would just install grub as the overall boot loader.  I believe that's what most of dual-booters use.  If at some point you decide you want to remove the Ubuntu, you can just fix the MBR using recovery console from your Windows disk.

---

### Post by LaurelLynn on 2007-04-14
Dear Ryokukitsune,

When using dd with the MBR the commands are:

$ sudo dd if=/dev/hda  of=someplacesafe   bs=512 count=1    (to save, your drive may not be hda)

$ sudo dd if=someplacesafe of=/dev/hda   bs=512 count=1    (to restore)

That count=1 is VERY important!  And don´t mix up if and of, or you can scramble the whole drive. Note: the first 446 bytes are the bootloader. The remaining bytes are the partation table, without which you are in real trouble.

thefoolisme is right.  I would seriously consider using GRUB as on boot all you have to do is hit enter or wait a few seconds to boot the default os, or use the keyboards up and down arrows to select it.

The biggest reasons for not using the Windows bootloader, is you have to figure out all the settings, and you probably won´ t have an option to boot in recovery mode when your done. Finally very few people even in the windows community know much about it.  I´ve only changed one once, and I´ve been supporting windows since there was such a thing. Most Windows people see it on their MCSE exams and forget it once they have passed.

By editing ¨/boot/grub/menu.lst  you can set windows as the default os, and shorten the wait time so that booting Windows just means turning it on and waiting an extra three seconds before it is ready.

At the top of the file is something like:

## defualt num
default     0

## timeout sec
timeout    5

Count down the grub entries (starting with zero) till you get to the Windows entry, try that number for default.  Or you could just take the Windows entry and move it to the top.  Set the timeout to something short and sweet like say  2 or 3 seconds (just leave enough time to hit the down arrow).

If you still feel you need the windows bootloader, I have a few MCSE study guides here with the basics, and I can look up the procedure for booting Linux on the net.

---

### Post by Ryokukitsune on 2007-04-14
i'de like to try grub as the primary boot loader i just dont know how to set that up. wingrub has failed me so many times... I thought i got it working today (after the Nth install of 6.10) but it disapointed me again u_u

now all grub does (wingrub) is flash the UI for a split second and displays something about a lst file. I actualy got it to load grub and it says something was wrong and it couldnt load =x

any thoughts?

---

### Post by LaurelLynn on 2007-04-14
Ok, have not had to try this myself, but it is right out of the ¨Linux Cookbook¨ (I take no resposibility for the outcome).

Backup the MBR first with the dd command above (the RIGHT one, check and double check it before hitting enter, the device must be the in file to save, ask us if you are at all unsure).

Also don´t store it on the drive you are copying it from, a USB stick works best (I have to point that one out, because some pretty smart people have made that mistake).

From the Live CD you run one of two commands, depending on whether you have a separate /boot partition.

$ sudo grub-install --root-directory=/boot  /dev/hda    (if you do, your drive may be sda, hdb, etc.)

OR 

$ sudo grub-install  /dev/hda                   (if you do not)

Then run:

$ sudo update-grub

If GRUB does not automatically add windows to it´s menu, the entry should be something like this

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

The hd0 part tells it the drive  so 0,1,2,3 are the same as the linux a,b,c,d and the ¨,0¨ is the partition number.

Let us know if there are any problems

---

### Post by Ryokukitsune on 2007-04-15
i'm just going to format my primary sata disk and start over. I figure there are two problems with this attempt at dual booting, my configuration and the fact that i'm trying to maintain Windows. if i remove windows as a factor i'm pretty sure i can make this easier to deal with ^^; I'll fallow the standard practice of primary disk partition. this way my head dosent explode from the frustration...

---

