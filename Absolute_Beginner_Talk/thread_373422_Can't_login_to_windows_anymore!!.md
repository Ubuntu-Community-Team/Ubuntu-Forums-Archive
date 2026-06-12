---
title: "Can't login to windows anymore!!"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-03-01
Hello,

I have been using ubuntu for a couple weeks now and I've been really satisfied so far. However, I do want to keep windows next to it for testing of .doc and .ppt files before sending them (as well as for a sense of security and peace of mind). 

I had it running next to each other perfectly. Now I reinstalled windows next to ubuntu. I knew that grub would not load anymore so I printed out this ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)) page before doing everything. 

So I followed the things under the heading "Using the Desktop/LiveCD and Overwriting the Windows bootloader". I reinstalled grub on /dev/hda1 (where windows is on and it was also the one with the star for it indicating it was the boot partition. 

However, now when I startup, and I want to select windows, it doesn't load windows, it just reloads grub. It doesn't restart the whole computer, it doesn't start windows, it just reloads grub. What rests me is choosing ubuntu. Which I don't really have a problem with, But I do need windows!!

Please help!

---

### Post by benfindlay on 2007-03-01
Could you please post the contents of the file you get when you type ```
sudo gedit /boot/grub/menu.lst
```

There may be something obvious in there that is amiss!

Cheers

---

### Post by kramer65 on 2007-03-01
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

-----------------------------------
I posted only the last part. I thought that all thos comments and other stuff was not neccesary..?

---

### Post by Kobalt on 2007-03-01
Could you please post the output of the following command line : 
```
cat /etc/fstab
```

---

### Post by kramer65 on 2007-03-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5   /media/hda5   vfat   iocharset=utf8,umask=000   0   0

Does that help?

---

### Post by Kobalt on 2007-03-01
I needed that so that I could know the number if your Windows partition. Can you access it in Ubuntu ? Is it the /dev/hda5 ?
If so, you have to set the partition number accordingly in you /boot/grub/menu.lst file. As it is set now, you windows partition would be hda1 (hd0,0 in grub). If it's actually hda5 then you should replace "root (hd0,0)" to "root (hd0,4)"...

---

### Post by kramer65 on 2007-03-01
Ehm... but hda5 is my fat32 partition where i have all my data. My windows is actually the hda1...

Any other ideas?

---

### Post by Herman on 2007-03-01
>  So I followed the things under the heading "Using the Desktop/LiveCD and Overwriting the Windows bootloader". I reinstalled grub on /dev/hda1 (where windows is on and it was also the one with the star for it indicating it was the boot partition.
> Ehm... but hda5 is my fat32 partition where i have all my data. My windows is actually the hda1...>  However, now when I startup, and I want to select windows, it doesn't load windows, it just reloads grub.You have installed grub to your Windows bootsector.

You should run Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run FIXBOOT command.

Then install grub to your hard disk's Master Boot Record (MBR).

Hint: The MBR is called (hd0), or /dev/hda

The first partition is (hd0,0) or /dev/hda1

So if Windows is hda1 *do not* install grub there. *Please*. :(

Do install grub to MBR. :)

Regards, Herman :)

---

### Post by kramer65 on 2007-03-01
Ah ok.

But to run recovery console I need to do it from within windows:

> With Windows running, insert the Setup CD into your CD-ROM drive. Start/Run/X:i386\winnt32.exe /cmdcons. Follow the instructions on the screen. 

So since I just installed windows I can also just reinstall and then  do that thrick from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) again, but now putting it on /dev/hda instead of /dev/hda1 right?

One thing. I can also just reinstall windows and then use the tips under "Using the Desktop/LiveCD while preserving Windows Bootloader" right? (I am wondering why I didn't do that in the first place.. :S)

---

### Post by cantormath on 2007-03-01
> **kramer65 said:**
> it doesn't load windows, it just reloads grub.

FANTASTIC! ME NIETHER!

---

### Post by Herman on 2007-03-02
I always though you could run Windows Recovery console from the 'Installation' CD, at least that's what I have learned from the reading I've done on the subject. I have a brand of computer that comes with the Windows 'Recovery' CD (as opposed to an 'Install' CD). The 'Recovery' CDs just format the entire hard disk and restore it to 'factory shipped condition'. There is no Recovery Console in a 'Recovery Disk', at least not the kind I have.
However, I use Windows with the FAT32 filesystem, not NTFS.
The FAT32 filesystem can be repaired by Linux. It is simply a matter of running a filesystem check with the appropriate options, and having the bootsector replaced with the backup bootsector. FAT32 has a backup of the bootsector to restore the bootsector with and I imagine NTSF would too, but it is probably not wise to try to manipulate it from Linux at this stage unless you add special software first.

Here is a link to explain that,                  [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup") .  Maybe that will help someone.

I guess re-installing doesn't hurt Windows, I used to re-install Windows  very often when I used to use it. My well know brand of antivirus re-assured me that "my computer was safe" since I was running their brand of antivirus software. An on-line scan found a bad threat that could have made my computer into a zombie and allowed the virus writer complete control of my computer. I tracked this malware down to a nice animated Christmas e-card from a cousin of mine who is a Microsoft tech support expert. It wasn't his fault, he had no idea it contained the malware. This came to light more than six months after I received the e-card, which came from a website which is run by a subsidiary of Micorsoft I think, so one would expect it to be safe. How come it took six months before this was even detected by any antivirus scan?  So I never did trust either Windows or antivirus vendors at all after that. I used to re-install it very often. I don't need it any more now, and certainly don't allow it on the internet. I just use it for doing experiments on, sort of like a 'guinea pig'.

One thing you need to understand, the MBR does not belong to Windows, it belongs to the owner of the hard disk, which is you or I.
The MBR is located in the first sector of the disk, sector 0. The MBR is made from the same material as the rest of the hard disk and can be written to and overwritten an infinite number of times.  We can install a little code that points to a bootloader to it and then overwrite that with another bootloader's code as many times as we like.


The first sector of an operating system partition is usually called the partition's 'bootsector', and in the case of Windows, it also contains bootloader code. In the case of a Linux OS partition, it isn't compulsory. You can install grub to a linux partition or to the hard disk MBR.
The Windows filesystem or whatever filesystem is in the first partition does not begin until sector 63, as the first track of the hard disk is left empty by convention, for the use of certain special types of software, like bootloaders. 

So the MBR and a bootsector are two completely separate places. They are similar in that they can all be written with (an appropriate) bootlaoder code.

If you install Windows bootloader to MBR and try to boot Linux with it, something it was never designed to do, you will need to do this manually and unless you know what you are doing it will be difficult. You will be placing yourself in a position where you may not get support from either Windows tech support or Linux forums, so you'll be on your own. You will also be stuck with a 'bare bones' bootloader with very limited capabilities and hardly any features.

If you install Grub to MBR it will be easier, you can let grub automatically configure itself in 99% of installations. I estimate around 500-600 a day are installing Ubuntu with grub, we have very few problems. The 'silent majority' have no problems at all. Most of the booting problems that are posted here in Ubuntu Web Forums are easily solved. Grub is a very versatile bootloader and boot manager, packed with features. It can be customized in many ways and even has its own command line interface, so it is really almost a small operating system in its own right.

The choice is yours,
Regards, Herman :)

---

