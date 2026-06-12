---
title: "Blank screen when attempting to boot"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Steve215 on 2007-05-04
I have an ATI X800 Pro video card and followed the directions located here: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) to get Ubuntu to boot with no luck. After doing the text install and choosing to boot Ubuntu at grub my screen goes blank and nothing happens. Anyone have any ideas how I can fix this?

I'm attempting to install Ubuntu 7.04 64Bit and using the alternate CD text installer. My system specs are:

AMD 3400+ (2.4GHZ)
1GB DDR Ram
ATI X800 Pro video card
250GB HDD with Windows XP
80GB IDE HDD with Ubuntu 7.04 installed with Grub setup to dual boot

---

### Post by ajmorris on 2007-05-04
go here: 

[http://ubuntuforums.org/showthread.php?&t=414194](http://ubuntuforums.org/showthread.php?&t=414194)


should do the trick, there is a bug with ati cards.

---

### Post by Steve215 on 2007-05-04
> **ajmorris said:**
> go here: 

[http://ubuntuforums.org/showthread.php?&t=414194](http://ubuntuforums.org/showthread.php?&t=414194)


should do the trick, there is a bug with ati cards.

Those were the directions I followed with no luck. Could the fix be different since I'm using the 64Bit version? :confused:

---

### Post by Steve215 on 2007-05-04
Things have gotten even stranger. If i boot into the recovery console and at the terminal type "gdm" it boots up like normal. After I enter login information and the desktop loads I get an error that says "Failed to initialise HAL!" Once I click OK everything appears normal. However, If I let Ubuntu boot normally my monitor turns off and nothing happens, nothing ever boots. Anyone have any clue what the problem could be? I've been working on this all night. :(

---

### Post by Steve215 on 2007-05-04
Apparently it's a bug with the AMD64 version of Ubuntu. If anyone else is experiencing this check out: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/86666)

---

