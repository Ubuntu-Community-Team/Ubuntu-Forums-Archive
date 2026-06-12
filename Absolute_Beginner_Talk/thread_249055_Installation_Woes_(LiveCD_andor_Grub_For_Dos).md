---
title: "Installation Woes (LiveCD and/or Grub For Dos)"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by cancel.man on 2006-09-02
_Machine:_
Toshiba Portege 7200CTe
600Mhz P3
192MB ram
11GB HDD, 6GB free
Current OS Win2K

I've attempted the installation through the regular/recommended route (booting into the CD-based environment then running the install from the desktop icon) but this causes the machine to simply hang with no end in sight. After clicking on the icon (double-clicking, hitting enter, whatever, all of the above), the icon is highlighted and the cursor does the cirlce thing and the CD/DVD drive starts running... and then just keeps running... the cursor disappears after a bit and nothing ever changes or happens but the CD keeps spinning and spinning.

Frustrated by this, I attempted the [Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows") approach using the bottom option (The CD Approach- copying the install CD to the HDD and using Grub). Unfortunately I've had no luck with that either. When I use the "Install Ubuntu" option on the first boot screen I get the message "Windows 2000 could not start because the following file is missing or corrupt: <windows 2000 root>\system32\ntoskrnl.exe."
Here's a copy of the boot.ini I'm trying to use:
```
[boot loader]
 timeout=30
 default=multi(0)disk(0)rdisk(0)partition(1)\grldr
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\grldr="Install Ubuntu"
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows 2000 Professional" /fastdetect
```

and the menu.lst:
```
title Install Ubuntu
 kernel   (hd0,0)/ubuntu/casper/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
 initrd   (hd0,0)/ubuntu/casper/initrd.gz
```

Notice I've modified both a bit from the instructions- especially menu.lst due to where the files are actually found on the current install CD. Unfortunately I'm still getting the same missing file error.

So any suggestions for getting either install method to work would be greatly appreciated. Thanks.

---

### Post by bodhi.zazen on 2006-09-02
I have no idea what you are doing or how to edit your windows boot.ini

However, the only thing i see is that it appears:
> multi(0)disk(0)rdisk(0)partition(1)\grldr="Install Ubuntu"
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows 2000 Professional" /fastdetect
? should they point to the same place? should windows be
```
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="Microsoft Windows 2000 Professional" /fastdetect
```

Just a wild stab in the dark.

---

### Post by cancel.man on 2006-09-02
Okay, got GRUB working (didn't have it configured properly- there are *much* better instructions on how to use it [here]("http://marc.herbert.free.fr/linux/win2linstall.html#loadlin-or-grub-for-nt")). Ubuntu still didn't install, but I'm going to play with a few things and see if I can work it out.

Once again, input and/or recommendations are welcome.

---

