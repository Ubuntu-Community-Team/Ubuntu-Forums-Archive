---
title: "Installing Ubuntu on Late 2010 MacBook Air 13&quot;"
date: 2018-02-23
forum: Apple Hardware Users
---

### Post by sultaan55 on 2018-02-23
So for the past few days I've been trying to boot Ubuntu and other Ubuntu-based distros like Mint and Elementary, but ive been running into a slew of issues. 
First off, I've been using the Mac Linux USB Loader to create a USB that would actually boot on Mac OS by adding in the UEFI-enabled kernel. However, every time I've tried installing the distro from the Live USB, it would go through everything right up until it was almost finished and then say that GRUB wasn't installed to the partition i had specifically set aside for it, leaving me without a compatible bootloader.


Seeing as this method is clearly not working, i was just wondering if there was any way i could actually install Linux at all. I have a USB drive, as well as a CD/DVD reader, I'm fine with completely erasing my system (I've accidentally done that three times now good lord), and i also have access to a Windows 10 machine, as well as other Mac OS devices if necessary.

My Mac is currently completely wiped, and im currently getting MacOS re-uploaded for the millionth time, so i will be starting from a clean slate. Any help would be greatly appreciated, and thanks in advance. :)

---

### Post by wildmanne39 on 2018-02-23
*Thread moved to **Apple Hardware Users, a more appropriate forum**.*

---

### Post by simply-selz on 2018-03-01
I've been using the instructions provided here:

[https://medium.com/@mmiglier/ubuntu-installation-on-usb-stick-with-pure-efi-boot-mac-compatible-469ad33645c9](https://medium.com/@mmiglier/ubuntu-installation-on-usb-stick-with-pure-efi-boot-mac-compatible-469ad33645c9)

I've gotten it up to where I'm suppose to install grub. Otherwise it boots with the option key and runs as well. The guide specifically warns you how not to destroy your mac installation: ubiquity --no-bootloader.

---

