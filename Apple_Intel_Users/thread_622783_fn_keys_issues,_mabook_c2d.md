---
title: "fn keys issues, mabook c2d"
date: 2007-11-25
forum: Apple Intel Users
---

### Post by joolz on 2007-11-25
Hi,

I have put the following line in /etc/modprobe.d/options:

options hid pb_fnmode=2

In order to use the functions keys by pressing the fn buttom. If not pressed, the F -keys are used. The thing is, it only works about 2/3 of the time booting up. I had no problem with this using Feisty.

Any ideas?

---

### Post by volanin on 2007-11-25
This is just a crazy wild guess, but...

1. Recheck if the line is correctly written in  the file **/etc/modprobe.d/options**
2. Run **sudo depmod -a**
3. Run **sudo update-initramfs -u**
4. Reboot and verify.

---

### Post by joolz on 2007-11-29
yes, sudo update-initramfs -u did the trick. thanks!

---

### Post by Rog-Mahal on 2007-11-29
I followed the same protocol and now my F1 and F2 keys don't affect screen brightness at all and I still have to press fn in order to get them to work as regular function keys. This problem only happens with the first 2 function keys. The others work fine, but still in the reversed manner (aka F3-5 are by default sound keys and you must press fn for normal behavior).

---

### Post by volanin on 2007-11-29
VERY strange!
It works perfectly here.
If you compiled your kernel using my config file, probably **hid** was compiled statically instead of as a module.
If that's the case, do the following instead:

**1.** Remove these lines from **/etc/modprobe.conf/options**.
**2.** Add the following: **hid.pb_fnmode=2** to your kernel options in **/boot/grub/menu.lst**
**3.** Run **sudo update-initramfs -u**.
**4.** Reboot and verify!

---

