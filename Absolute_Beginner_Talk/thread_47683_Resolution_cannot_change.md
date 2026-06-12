---
title: "Resolution cannot change"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by noid1037 on 2005-07-09
Today on a new HD, Ubuntu was installed.  I am using the OS to access the internet now.  The issue I am having is that I cannot change the resolution.  The preferences are not able to change from the 640*480 @ 60 Hz.  I went to the xorg.conf and dont know what I am looking for... can someone give me a hand?
[email]linux@baycrestfl.com[/email] <direct

Thanks all.... can wait to check out more of the OS!

---

### Post by Williams477 on 2005-07-09
I had the same problem. There are alot of things are on the forums that you can look up to show you how to fix it but I only had success with one.

Go into your terminal and load the xorg.conf. Look for this script:

> Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver **"i810"**
BusID "PCI:0:2:0"
EndSection

Change "i810" to "vesa." You can also try plugging in your refresh rates and sync rates but I had no luck with that and it only caused my Ubuntu to crash.

---

### Post by noid1037 on 2005-07-09
Silly question being a newbie.. how do I open the file in term?

Thanks

---

### Post by Williams477 on 2005-07-09
Depends, to open xorg.conf use the following command:

> sudo gedit /etc/X11/xorg.conf

To open another file, like a install file, open the terminal, and type the location of the file. For example:

> /home/username/desktop/fire-fox install/install firefox

---

### Post by noid1037 on 2005-07-09
The vesa worked great thanks for the input!

Loving the new OS!
Noid

---

