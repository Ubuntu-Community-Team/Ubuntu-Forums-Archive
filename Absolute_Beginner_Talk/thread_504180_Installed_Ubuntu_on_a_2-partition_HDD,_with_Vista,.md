---
title: "Installed Ubuntu on a 2-partition HDD, with Vista, now Vista won't boot"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Davers! on 2007-07-18
So basically I have ONE hard drive connected to my system a 250GB SATA drive.

It had 2 partitions before the Ubuntu install, both about 116GB. Upon installing Ubuntu, I deleted my XP partition, and created a 5GB swap partition and the rest as my ext3 root partition.

"/dev/sda1" is my linux swap partition.
"/dev/sda3" is my ext3 root "/" partition.
"/dev/sda2" is my ntfs "/media/sda2" Vista partition. I can browse it in Ubuntu and access my files. according to gparted, this partition has "boot" as a flag.

My boot menu.lst is as follows:

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52830b9e-d19f-44b3-8c8b-1522366f5585 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52830b9e-d19f-44b3-8c8b-1522366f5585 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=52830b9e-d19f-44b3-8c8b-1522366f5585 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=52830b9e-d19f-44b3-8c8b-1522366f5585 ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

#title		Ubuntu, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

title		Microsoft Windows Vista Ultimate
rootnoverify  	(hd0,1)
makeactive
chainloader    	+1
```

I commented out those entries to keep it clean. Upon trying to boot to Windows, I get "BOOTMGR is missing - Press Ctrl+Alt+Del to restart".

What's wrong?

---

### Post by Davers! on 2007-07-18
bump

---

### Post by Davers! on 2007-07-19
bump

---

### Post by playme123 on 2007-07-19
you may have deleted the bootloader for your vista

---

### Post by Davers! on 2007-07-19
I don't think I did, but even if it somehow got removed, shouldn't it still boot to Vista from GRUB? That's what I'm trying to do. When I select Vista from GRUB, should it go to the Vista boot loader or just straight to Vista?

---

### Post by confused57 on 2007-07-19
If you have a Vista Install DVD, this may help:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You can always reinstall grub, using the Ubuntu live cd, if the mbr gets overwritten:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by AlexenderReez on 2007-07-19
hm...i also using ubuntu dual boot with vista(ultimate)...i never face this problem but surely it problem cause from your installation...i think you made mistake without realizing it while installation process...i think you still can recover vista using vista  installer cd ...there is option upgrade right?..but i'm not sure that option can be use or not without booting to vista...

---

### Post by Nevis on 2007-07-19
I think that's exactly what happened. Vista boots very differently than XP and basically insists on taking over the boot process. See the links below for more info;

[Ubuntu Help - Windows Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot")
[Vista/Ubuntu dual boot how-to]("http://ubuntuforums.org/showthread.php?t=371530&highlight=dual+boot+vista")

I think you'll need to use the Vista cd to restore the boot manager then configure it to show Ubuntu as an alternative OS choice. In other words, you'll be using Vista's bootloader instead of Ubuntu's bootloader GRUB.

---

