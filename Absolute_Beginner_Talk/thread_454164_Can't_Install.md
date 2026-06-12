---
title: "Can't Install"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by rcdeacon on 2007-05-25
I need some help! I cannot install Unbuntu, Kubuntu or Unbuntu CE on my machine. It is a Dell Dimension 4600 with 1g ram, a Nvidia Geforce 5500 video card and some usb peripherials along with a samsung lcd monitor. This problem is unique to Unbuntu because I can install Mepis and PCLOS just fine. The initial splash screen comes up and it appears to be searching out the hardware and then I get the following error message.  &quot;busyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash) Enter 'help' for a list of built-in commands.  /bin/sh: can't access tty; job control turned off (initramfs) [ 56.711912] ata2.01: failed to set xfermode (err_mask=0x4)&quot;  I have tried changing the resolution using the f4 key to no avail. I really want to put Ubuntu on my box but I am literally at the end of my knowledge level and close to being at the end of my rope with Ubuntu. Hope someone can help with this.  EDIT: BTW I am talking about 7.04 Fiesty

---

### Post by justifier on 2007-05-25
did you burn the CD yourself? 

if so try burning a new one, sounds to me like a package error.
reduce the burn speed, often helps too.

---

### Post by rcdeacon on 2007-05-25
Actually I have burned about 3 cd's the latest was burned at 4x.

---

### Post by SusieK on 2007-05-25
Hi

I had big problems trying to install Ubuntu, whether by downloading it or using a CD. Each time there were different error messages and it nearly drove me to suicide.

Finally managed to get it installed and running by downloading the Wubi installer from here:  [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html).

 Even that took a few goes, but it did work eventually. Can't be of any more help as I'm a complete novice, but if it worked for me, maybe it will oblige for you.

---

### Post by Terl on 2007-05-25
You may want to check [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107976") for more info and possible work arounds.

---

