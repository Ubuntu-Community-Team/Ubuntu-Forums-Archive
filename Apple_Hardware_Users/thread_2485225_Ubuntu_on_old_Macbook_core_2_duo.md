---
title: "Ubuntu on old Macbook core 2 duo?"
date: 2023-03-23
forum: Apple Hardware Users
---

### Post by smokeybear on 2023-03-23
Hello.
I have old Macbook 2ghz core 2 duo 4gb ram ddr2 with mac os x 10.5.8 on it. I can't even open web pages on it because nothing can be updade anymore (thanks apple). I thought I might try to install Ubuntu on it so I can at least use it to watch YT videos. The thing is that I can't create Ubuntu bootable USB on mac but I have old laptop with Win 7 on it (everything works just fine on that one). My question is, is it possible to create Ubuntu bootable USB on that Win laptop for the installation on the old mac? And if yes, how? I tried to look for it on the web but I can't find anything. I used balenaEtcher to flash usb with ubuntu-22.04.2-desktop-amd64 iso but both Win and OS X won't recognise the USB. I tried rufus-3.21 but that just creates bootable for PC. Any ideas?

---

### Post by oldfred on 2023-03-23
Know nothing about Mac.
Is this 32 bit UEFI. PCs with Core2duo were 64 bit but only BIOS boot. Apple was the first with efi, later UEFI.
Ubuntu now is 64 bit only.

While 4GB of RAM should run Ubuntu, you many want a lighter version for an old system.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

Installed Lubuntu 18.04 LTS on a MacBook Air 1,1 (early 2008) 
[https://ubuntuforums.org/showthread.php?t=2402179](https://ubuntuforums.org/showthread.php?t=2402179)
Old Mac with core2duo & 32 bit UEFI
[https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

---

