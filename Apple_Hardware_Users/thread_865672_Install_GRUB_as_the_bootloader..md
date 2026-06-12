---
title: "Install GRUB as the bootloader."
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by r0b0t1 on 2008-07-20
Ok, so just recently I've realized REFIt is pretty ****** up on my machine. I've read this thread about installing GRUB ([http://ubuntuforums.org/showthread.php?t=233243](http://ubuntuforums.org/showthread.php?t=233243)) but it did not work/help. For one, I have a 64bit machine, and I can't find the 64 bit version of GRUB.

---

### Post by hajk on 2008-07-21
You have to provide more info on what went wrong, because by default the Ubuntu installer already installs grub to the MBR of your hard drive, no need to do that afterwards or to worry about the right version of grub.

As to rEFIt, this can be installed in several ways. Easiest is to boot Mac OS X, download the latest .dmg from the rEFIt site at SourceForge, then install it with its own installer using all the defaults. Open a terminal and enable it with the command```

$ sudo /efi/refit/enable-always.sh
```
Rebooting shows the rEFIt boot menu with an Apple icon (the default) and a Penguin icon (for Ubuntu). Don't boot the Penguin just yet: use the arrow key to select the rEFIt Partitioner Tool to synchronize the MBR and the GPT partition tables; then choose rebooting the computer. The next time the rEFIt boot menu appears, the Ubuntu icon can be chosen to boot. 

Some people triple-boot with Windows as a third OS, i.e. they install Windows after Ubuntu, thereby overwriting the MBR. This requires reinstalling grub to the MBR and redoing the synchronizing bit. Let us know if this is your problem.

---

### Post by cyberdork33 on 2008-07-21
refit is not really a replacement for grub. Grub is still used to boot the linux kernel even with refit enabled. Try to describe what issue you are having with refit...

---

### Post by r0b0t1 on 2008-07-21
Well, OK, now I'm calmed down a little. Well, anyway, my problem with rEFit is when I try to install Windows then Linux, Windows says that it can not find HAL.dll, or, when I fix boot.ini, that it is unable to mount the partition. If I install Linux and then Windows, the Linux entry in rEFIt is removed, and I am unable to access it.

So, in short, is there any way I can skip rEFIt and go strait to GRUB?


P.S.: Also, in my Windows partition there is the little problem of boot.ini being locked. Any way to override this? (This is a problem with computers... I mean, if you're looking for that file anyway, don't you know what to do?)

---

### Post by cyberdork33 on 2008-07-22
> **r0b0t1 said:**
> Well, OK, now I'm calmed down a little. Well, anyway, my problem with rEFit is when I try to install Windows then Linux, Windows says that it can not find HAL.dll, or, when I fix boot.ini, that it is unable to mount the partition. If I install Linux and then Windows, the Linux entry in rEFIt is removed, and I am unable to access it.

So, in short, is there any way I can skip rEFIt and go strait to GRUB?
Well these problems have nothing to do with rEFIt. ALl rEFIt does is give you a nice menu for the bootable options on your Mac. It sounds like it is working fine. 

You get a hal.dll error because the partitions have changed on the disk after you installed Windows (it doesn't like that). 

The linux icon dissapears because windows' bootloader overwrites grub in the MBR.

you should create all your partitions upfront before installing anything, and you should tell the Ubuntu installer to install grub to the Ubuntu root partition (this is done with the "Advanced" button just before the installer actually starts installing files.)

---

### Post by r0b0t1 on 2008-07-22
I picked the default options, so where is it installed now? Do I have to reinstall to do this?

---

### Post by cyberdork33 on 2008-07-22
> **r0b0t1 said:**
> I picked the default options, so where is it installed now? Do I have to reinstall to do this?
I was talking about what to do if/when you install in the future. 

Is your windows partition working now? if not, then I would get that working first, then you can reinstall grub from the live cd:

[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by r0b0t1 on 2008-07-23
Thanks. I think that is the thread that will answer all my problem.

---

