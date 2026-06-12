---
title: "Problem with GRUB Boot loader on Ubuntu 20.04- dual boot on MacBook Pro"
date: 2020-08-19
forum: Apple Hardware Users
---

### Post by nansk on 2020-08-19
I'm trying to dual boot my Mac (2018 MacBook Pro running MacOS Mohave 10.14.6) with Ubuntu 20.04 with a USB installation. I'm following the steps [here]("http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf") to install Ubuntu without using rEFIt as I couldn't properly install rEFIt on my computer. However, I can't seem to get through part 4, particularly the "grub-mkconfig -o boot/grub/grub.cfg" step. When I type in the command on terminal, I get this error message: "cannot find a GRUB drive for /dev/sda1. Check your device.map"
[ATTACH=CONFIG]286772[/ATTACH]

This is how I edited my partitions when installing:
[ATTACH=CONFIG]286773[/ATTACH]
And this is what my disk utility on MacOS looks like:
[ATTACH=CONFIG]286774[/ATTACH]
I allocated 100 GB of space for Ubuntu and 16 GB RAM, so it looks like disk0s6 and disk0s3 are my Ubuntu installation (I named it "Ubuntu Data" but for some reason that name also doesn't show up).
What can I do to solve this?

---

### Post by oldfred on 2020-08-19
Moved to the Apple sub-forum for better fit.

Do not know Mac.

But with PC, you need UEFI update & SSD firmware update.

Many with Mac use rEFInd which has replaced refit.

[https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind](https://askubuntu.com/questions/831161/dual-booting-os-x-or-macos-with-linux-without-refind)

With An Out-Of-Tree Kernel Patch You Can Finally Read/Write To The SSDs On Newer Macs - 2019 July
[https://www.phoronix.com/scan.php?page=news_item&px=MacBook-Finally-Linux-SSD-RW](https://www.phoronix.com/scan.php?page=news_item&px=MacBook-Finally-Linux-SSD-RW)

Upgrade Mac
[https://support.apple.com/en-us/HT206886](https://support.apple.com/en-us/HT206886)
Linux on mid-2017 MacBookPro
[https://nixaid.com/linux-on-macbookpro/](https://nixaid.com/linux-on-macbookpro/)

---

### Post by danish-bronco on 2020-08-26
Don't know if it's any help, but I also installed (X)ubuntu on a MacBook Pro (early 2006, so32-bit only) and I opted for rEFInd as boot manager (not bootloader), and during install, grub was installed on dev/sda, not dev/sda1 or any other partition, and it boots very well, albeit with a hiccup here and there that has probably to do with the graphics driver crashing more than anything else.

---

