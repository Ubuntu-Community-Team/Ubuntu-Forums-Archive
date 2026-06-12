---
title: "Installed Ubuntu, how do I boot to it?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by ccclairee on 2007-08-18
I installed Ubuntu on my second HDD. Now when I start up, it boots straight to windows. No option to boot to Ubuntu. I thought Windows boot manager should be allowed to take over, to keep windows "stable", correct? How do I access it? Or do I need to install a boot manager...

---

### Post by taurus on 2007-08-18
You need to install GRUB, bootloader, to MBR when you install Ubuntu so you can boot either Windows or Ubuntu.

---

### Post by Max Luebbe on 2007-08-18
Sounds like GRUB got put in the mbr of your secondary disk instead of your primary, which isnt helping because the computer boots off the primary.

You need to install grub into the mbr of the primary drive.

---

### Post by ccclairee on 2007-08-18
If I install Grub, will it hurt my Windows installation?

How do I install Grub in the mbr of my primary drive? By primary, do you mean the drive Windows is on?

---

### Post by taurus on 2007-08-18
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by ccclairee on 2007-08-18
I read the help files.

Windows in installed on dev/sda and Ubuntu is installed on dev/hdb1

If I make a Grub boot disk and install from there, which disk do I install it on?

---

