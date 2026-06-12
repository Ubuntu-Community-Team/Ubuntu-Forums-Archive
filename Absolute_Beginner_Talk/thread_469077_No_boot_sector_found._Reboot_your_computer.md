---
title: "No boot sector found. Reboot your computer"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by wordsmithereens on 2007-06-09
Lost boot sector on Ubuntu 7.04 install. 

I have a single-boot drive that displays the message in the title. How can I restore the boot sector?  I have a live CD for 7.04

Thanks!

~wordsmithereens~

---

### Post by st33med on 2007-06-09
Are you talking about the first partition on your hard-drive? Can you still boot up with a CD? Can you access BIOS?

---

### Post by wordsmithereens on 2007-06-09
> **st33med said:**
> Are you talking about the first partition on your hard-drive? Can you still boot up with a CD? Can you access BIOS?

Hi;

I can boot to CD. 

Hard disk partitions appears to be OK via GPARTED  from  Live CD. /dev/hda1 , /dev/hda2 , and /dev/hda5 all appear to be OK.  I seem to have lost the boot sector and need to restore or recreate it.

---

### Post by st33med on 2007-06-09
Try reinstalling Ubuntu.

---

### Post by wordsmithereens on 2007-06-09
> **st33med said:**
> Try reinstalling Ubuntu.

Surely there is a more elegant solution than that?

---

### Post by wordsmithereens on 2007-06-09
> **wordsmithereens said:**
> Surely there is a more elegant solution than that?

Whew!  It turns out there was a far more elegant solution: 

I needed to recreate  GRUB 

1. Boot to live CD
2. Start a terminal 
3. run the following code in terminal 

```

sudo grub
root (hd0,0) 
setup (hd0)
quit

```

4. Shutdown
5. remove LiveCD
6. Reboot

I hope that will help someone else with the same problem.

---

### Post by Herman on 2007-06-09
There is considerable confusion between the meaning of the terms 'bootsector' and 'MBR'. :D

Often these terms are used interchangeably especially by Microsoft Windows enthusiasts, who like to make believe that Windows actually owns the MBR of everyone's hard disk, and that installing Grub can somehow damage Windows. They tend to prefer not to distinguish between what is and is not part of their Windows operating system.

What I call the MBR is the first sector, or sector [FONT=System]0[/FONT] of the hard disk, which is the first sector of the first track, which is unformatted and not part of any file system and does not belong to any operating system.
A 'boot sector' is the first sector of a partition. If it's a Windows bootsector, then Windows bootloader's IPL will be installed there by default. If it's the first sector of a Linux partition, it is usually a good idea to install the IPL for either Grub or Lilo there yourself, as this is not done by default, and it can help you boot in an emergency.

You can see for yourself by typing 'sudo fdisk -lu' into a terminal, and you will see that the first sector of your first partition is not unitl sector number 63. ```
sudo fdisk -lu
```If you want to install the IPL for Grub to the first sector of your Ubuntu partition and if your Ubuntu partition happens to be partition number 1 you would do,
(do not do this if Windows happens to be partition 1 on your disk though!!!) 
```
sudo grub
root (hd0,0)
setup (hd0,0)
quit
``` That doesn't re-create grub, Grub is actually in your /boot/grub directory in your Ubuntu partition. That only install a small amount of code that makes your MBR or your bootsector point to Grub.

You can actually delete and re-create Grub, (meaning the entire contents of your /boot/grub directory) if you really want to for some reason. For example 
```
sudo rm /boot/grub/*
ls /boot/grub
sudo grub-install /dev/hda1
sudo update-grub
ls /boot/grub
``` That would re-create Grub.

Some of this might seem to some people like I'm being really fussy and nit-picking over the use of terms here, but some other people might think it's interesting.  I hope it helps a few people to understand things a little better.
Regards, Herman :D

---

### Post by wordsmithereens on 2007-06-09
> **Herman said:**
> There is considerable confusion between the meaning of the terms 'bootsector' and 'MBR'. :D

Often these terms are used interchangeably especially by Microsoft Windows enthusiasts, who like to make believe that Windows actually owns the MBR of everyone's hard disk, and that installing Grub can somehow damage Windows. They tend to prefer not to distinguish between what is and is not part of their Windows operating system.

... <snip>

Some of this might seem to some people like I'm being really fussy and nit-picking over the use of terms here, but some other people might think it's interesting.  I hope it helps a few people to understand things a little better.
Regards, Herman :D

That IS interesting and useful - thanks for the clarification.  The confusion probably extends to the BIOS vendor as well - I was taking the message literally. 

I still wonder why running the sequence of grub code fixed the problem?  Maybe the BIOS does not differentiate WHY a disk does not boot? 

I'm just happy I didn't need to reinstall and copy files from backup. :)

~wordsmithereens~

---

### Post by Herman on 2007-06-10
Yes, wordsmithereens, the confusion is very deep and widespread and I guess it it's just one of many ambiguities to do with computers.  Error messages of all kinds generally seem to be notoriously inaccurate and more than half the time can be downright misleading.

I'm happy for you too that you had no problems getting your Ubuntu booting again.  :D 

It's a shame that such confusion continues, because the misunderstanding can cause some people to mistakenly install Grub (or rather the IPL for Grub), to their Windows boot sector when they are dual booting if they don't know the difference between their boot sector and their MBR. It happens every now and then, and it gives Grub a bad name which is totally undeserved, especially if they don't know how to fix their boot sector again (FIXBOOT instead of FIXMBR). Some people can become so distressed that they panic and re-install Windows, sometimes without even rescuing their data first. (If they aren't very experienced computer users).

I think my usage of these terms is in accordance with the information in the Gnu/Grub Manual. For example in this link, [3.2 Installing GRUB natively]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively"), if you read the same terms in the context of that link you would see what I mean. (Just so people know it's not just me imposing my own personal opinions and you all). :D

> I still wonder why running the sequence of grub code fixed the problem? Maybe the BIOS does not differentiate WHY a disk does not boot? No, you typed 'setup (hd0)', which designates the MBR of your first hard disk to Grub. The BIOS always looks at the first sector of the first hard disk for a bootable disk signature and some boot loader code to start booting from. Without that the BIOS would move on and look at whatever device is next in your boot priority in your BIOS, or give you an error message. The BIOS doesn't know how to boot an operating system by its boot sector at all. 
If you had typed (hd0,0) you would have told Grub to install its IPL to the first sector of your Ubuntu partition and you would still not be able to boot until you install Grub or some other boot manager in your MBR.
If you had a second hard disk you could have installed the IPL for Grub to the MBR of that with 'setup (hd1)', but the BIOS wouldn't look their either unless you force it to. You could do that by pressing your F8 or F12 key as your computer boots up and selecting your second hard disk from the list of bootable devices. Most, but not all computers have that ability, for example, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key")

Regards, Herman :D

---

