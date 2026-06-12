---
title: "Grub Error 21"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by revengeofthecow on 2007-01-15
Hey, all, thanks in advance for helping me out. I have Ubuntu 6.10 and Mandriva 2007 installed on an external hard drive (/dev/sdb) , with Windows on my main hard drive (/dev/sda). Before I installed Mandriva, Grub only loaded when the external hard drive was plugged in; when it was not, Windows automatically booted. Very good for me, seeing as I prefer Windows for use in classes and I don't want to carry around my external drive.

So after I installed Mandriva, I was able to continue using the Grub bootloader I had installed with Ubuntu. I got the Mandriva entry working right, but there's one problem. If the external hard drive is unplugged, I get a message "Grub loading, please wait... Error 21". A bit of Googling revealed that this shows a problem with BIOS recognizing the disk, but that doesn't help me solve the problem. What can I do? Would a reinstallation of Windows solve the problem? I don't really want to, I have it configured really well. How can I get Windows to boot automatically without the external drive plugged in?

Here is a copy of my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=027dea0d-e48b-48ae-80cf-13c58c3a100f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=fabd4ad2-97dc-484c-a232-fcc022178a05 none            swap    sw              0       0
/dev/sda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

```

And here's my menu.lst:

```
title		Ubuntu 6.10
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu 6.10 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# Entry for Mandriva 2007
title		Mandriva 2007
kernel (hd0,4)/boot/vmlinuz root=/dev/sdb5  resume=/dev/sdb6 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd1,0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows System Recovery
root		(hd1,1)
chainloader	+1
```

Thanks much.
-Greg

---

### Post by peabody on 2007-01-15
It kind of sounds like you didn't have grub installed in the MBR of your internal harddrive, but rather, of the external hard drive, and your external was being booted from the bios when plugged in.  Was that the case?

---

### Post by rejser on 2007-01-15
you don't need to reinstall windows. if you start the installer and go to recovery mode you can use bootfix (i think it's called), this will make windows boot by default. 
Downside is that ubuntu won't boot when plugged in. Guess you can install grub to /dev/sdb and not to sda and it would work.

---

### Post by ucsdrake on 2007-01-15
hey revengeofthecow i also get the Error 21 but am wondering .. where did you install the GRUB to start and is windows on youre external HDD at all?

---

### Post by revengeofthecow on 2007-01-15
Hey, all, to answer your questions I originally put Grub on sdb, in the hopes that Windows would boot without Grub when the hard drive was not plugged in, which was happily the case. Perhaps it's trying to access Grub and failing. I will try that bootfix solution and get back to you all.

Oh, and Windows is on my internal hard drive. Not on my external at all. I'm not that good a hacker :rolleyes:

By "start the installer" do you mean the Live CD? And do I just open an instance of Terminal and type bootfix? Or do I need to be in Grub int he terminal to do that?

---

### Post by peabody on 2007-01-15
> **revengeofthecow said:**
> Hey, all, to answer your questions I originally put Grub on sdb, in the hopes that Windows would boot without Grub when the hard drive was not plugged in, which was happily the case. Perhaps it's trying to access Grub and failing. I will try that bootfix solution and get back to you all.

The fixboot thing should solve the problem then, although you may to reinstall grub to your external (can't say for sure, try it out first).

---

### Post by revengeofthecow on 2007-01-15
OK, so what exactly do I type? I'll open an instance of Terminal in the Live CD and switch to Grub to edit it, then what?

---

### Post by peabody on 2007-01-15
To reinstall grub or do the fixboot thing?  Don't worry about grub for now, do the fixboot thing from the xp recovery cd.

---

### Post by revengeofthecow on 2007-01-15
I can't do the fixboot thing. The notebook is a Gateway tablet; the recovery CD only includes options for reinstalling the operating system, wiping the hard drive. Is there something I'm missing? If not, is there an alternative solution?

---

### Post by confused57 on 2007-01-15
> **revengeofthecow said:**
> I can't do the fixboot thing. The notebook is a Gateway tablet; the recovery CD only includes options for reinstalling the operating system, wiping the hard drive. Is there something I'm missing? If not, is there an alternative solution?

You might want to look into the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Check out the section "Situations where Super Grub Disk is useful", one of which is to restore Windows mbr.

If you have a floppy drive, you could use a Win98SE boot floppy to restore your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot Windows, you might be able to reinstall grub onto your external drive mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Before reinstalling grub to your external drive mbr, set your computer to boot first to the external hard drive...once you're able to boot Ubuntu, then you could add an entry to your menu.lst to boot Windows from grub(but you'll need to use mapping commands).

---

### Post by jimrz on 2007-01-15
> **revengeofthecow said:**
> I can't do the fixboot thing. The notebook is a Gateway tablet; the recovery CD only includes options for reinstalling the operating system, wiping the hard drive. Is there something I'm missing? If not, is there an alternative solution?

are you sure? thought there was a "repair" option on the cd., you might try calling Gateway support to find out how to get to it. if you do find the repair option the command is ```
fixmbr
```

---

### Post by revengeofthecow on 2007-01-16
So the problem's solved. I put all my data in Linux and reformatted. Apparently my computer needed it, I got a huge speed boost in Windows... silly OS :D. Anyway, thanks all for your help. I'll definitely look into Super Grub Disk for next time I screw up my MBR (which will probably be sometime next week!).

---

