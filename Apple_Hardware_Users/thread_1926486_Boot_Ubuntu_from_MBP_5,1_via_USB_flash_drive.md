---
title: "Boot Ubuntu from MBP 5,1 via USB flash drive"
date: 2012-02-16
forum: Apple Hardware Users
---

### Post by FischersFritz on 2012-02-16
I tried booting into Ubuntu 11.10 (64-bit) by following the instructions as provided on the ubuntu-download site, also with rEFIt. However, I always end up with an error message "missing operating system". Using a CD is no option since the optical drive is gone.

Any hints?

---

### Post by gemini44 on 2012-02-19
hi m8,
i found this link for update ozc ssd update method using efi for boot ubuntu livecd. i have a mbp7.1 and i m using ubuntu 11.10-64 bit iso and it works flawlessly. (also i tried mint 64 bit live dvd works like a charm but when i install to my ssd it isnt boot anymore :( ) just try. ;)

1. Download ISO 2 USB EFI Booter for Mac (see below)
2. Format a USB drive "MS-DOS FAT" with a MBR scheme using OS X Disk Utility
3. Create a directory /efi/boot on the USB drive
4. Copy the file bootX64.efi from the ISO 2 USB EFI Booter for Mac into the /efi/boot directory on the USB drive
5. Also copy the Ubuntu 11.10 64-bit .iso file into /efi/boot/ on the USB drive, and rename it to boot.iso
 
iso to efi link: [http://www.mediafire.com/?dpgorsfdkf6nn2c](http://www.mediafire.com/?dpgorsfdkf6nn2c)

full article: [http://www.ocztechnologyforum.com/forum/showthread.php?92009-Updating-firmware-of-Vertex-3-Agility-3-Solid-3-drives-on-2011-Macs-using-a-Linux-CD](http://www.ocztechnologyforum.com/forum/showthread.php?92009-Updating-firmware-of-Vertex-3-Agility-3-Solid-3-drives-on-2011-Macs-using-a-Linux-CD)

---

