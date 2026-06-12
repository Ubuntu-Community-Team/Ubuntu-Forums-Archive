---
title: "Successful Ubuntu 10.10 Boot on Macbook Pro 5,3"
date: 2011-04-12
forum: Apple Hardware Users
---

### Post by GTOkid on 2011-04-12
Hi guys,

Thought that I would share my story of trying to get a USB thumbdrive to boot ubuntu on my MacBook Pro.

I originally bought a 32Gb flash drive thinking that it would be as simple as throwing ubuntu on and pressing go. I soon found out the hard way that Apple won't let you boot BIOS(Legacy) OS's from a thumbdrive. A long learning curve later, I could successfully boot the ubuntu **Kernel** from my thumbdrive alone. I partitioned my drive into 4 partitions an EFI boot partition(1) a fat32 boot partition(2) an ext4 filesystem(3) and a HFS+ rEFIt partition(4). After following the steps put forth on [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook) I was able to configure grub to properly load the ubuntu kernel, however, it would crash every time i tried booting. I edited my grub.cfg file to load /bin/sh on startup, and that got me to boot into an SH shell, but nonetheless startx would not properly load. A headache and a half later, I discovered that ubuntu does NOT like being booted from EFI.

I could have continued these shenanigans and tried to get ubuntu to boot using EFI, but I took the lazy route out. Apple does not let you boot USB from BIOS, but it does, however, let you boot CD's from BIOS. I burnt a copy of the "Super GRUB2 Disk" from [www.supergrubdisk.org](www.supergrubdisk.org). Poped it in my CD tray, held 'C' when booting, grub2 loaded, pressed 'detect os' and viola: it booted. Everything works great, video drivers, usb drivers, everything is exactly like if ubuntu was on my HD, and to be honest the speed is GREAT - i would almost go far enough to say that it is faster than booting from a HD, the only issue is that without a SWAP partition, the memory fills up rather fast, and sometimes you have to wait for that to catch up.

To recap for the lazies who dont want to sift through my wall of text:
Step 1: Install Ubuntu to a thumbdrive just like you would a HD
Step 2: Burn the "Super GRUB2 Disk" from [www.supergrubdisk.org](www.supergrubdisk.org)
Step 3: Hold 'C' when booting -> detect OS's
Step 4: Boot from Ubuntu on you Flashdrive, Enjoy!

---

### Post by edmondt on 2011-04-13
nice workaround :)

---

### Post by GTOkid on 2011-04-13
Thanks. :)

Now I am trying to get grub2(efi) to chainload grub2(bios) which would then load ubuntu. If I can get this working, it would eliminate the need for the CD.

---

