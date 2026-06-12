---
title: "Help, Installed ubuntu 12.04 now cant access Mac OS Lion"
date: 2012-05-26
forum: Apple Hardware Users
---

### Post by Aleator on 2012-05-26
Hi everyone,

long story short, I installed Ubuntu 12.04 today on my Mac Book Pro, previously it has been dual booting Mac OSX and Windows 7 via the bootcamp. Since I have installed ubuntu i can no longer access the other two OS'. Specifically when I select Mac from the Grub2 menu, the screen just goes black and nothing happens. If i select windows7 from the menu it says invalid OS.

 I only have one harddrive that is partitioned amongst the OS'. Gparted shows
/dev/sda1, Fat 32, /mnt/boot-sav/sda1, EFI, flag boot
/dev/sda2, hfs+,   /mnt/boot-sav/sda2, Macintosh HD, flag boot
/dev/sda3, hfs+,   /mnt/boot-sav/sda3, Recovery HD
/dev/sda4, ntfs,    /mnt/boot-sav/sda4, Bootcamp
/dev/sda8, ext4,  /                                       
/dev/sda6, ext4,    /mnt/boot-sav/sda6, Ubuntu

Additionally i know all the files for the other OS'  are still there as i can see them in file manager.  Also i cannot boot from CD, it flashes the traditionally white mac screen on start up for approx 1 second before going to the grub 2 bootloader. 


any help would be much appreciated

thanks heaps

---

### Post by kc1di on 2012-05-26
haven't do this my self but this article may be of help.
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required")

---

### Post by Aleator on 2012-05-26
thanks for the help but the issue is that I have already installed the three os', so I cant go back and install rEFIt. I also cant access mac whatsoever to install it.



I probably should have looked at the tutorials  before installing, just assumed it would be the same process as on a pc.

---

### Post by kc1di on 2012-05-26
Ok , did you get any kind of restore disk with the Mac pro book?

if you did try and restore the boot loader for Mac and the go from there.

---

