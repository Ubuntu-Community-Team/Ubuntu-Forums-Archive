---
title: "enable resytricted driver without internet"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bibas on 2007-11-20
i have  "ATI RADEON XPRESS 200 series graphics card" which doesnt work in ubuntu.
I dont have access to internet in ubuntu either.
How do i make graphics to work?

Expecting kind help soon .

---

### Post by jpittack on 2007-11-20
An open source driver is installed by default.  If you don't have access to the internet, you won't be able to use ati's driver.  If you download the driver on another computer and transfer it to your Ubuntu computer, there is a guide called ATI Driver for Dummies you can use.  Could you explain if you are going to be using compiz or any 3-d.

---

### Post by bibas on 2007-11-20
thanks for quick reply.

I got ubuntu just because i had read about its 3d(box like)  efffect.
Iam trying to get used to it and have no plans to use other softwares yet.

would u please tell more about the "for Dummies" thing and where can i get it?

---

### Post by jpittack on 2007-11-20
[http://ubuntuforums.org/showthread.php?t=575843&highlight=ATI+driver+for+dummies]("http://ubuntuforums.org/showthread.php?t=575843&highlight=ATI+driver+for+dummies")

A good starting point.  I suggest using the 8.37 driver and then installing xserver-xgl, altough I would not know where to find it, since I have always gotten it through the package manager.  If you want to learn about installing driver with complications, try the newest driver, 8.42.3.  If you are using 64 bit, your 2-d will slow down, and firefox may have scrolling issues.  If you are 32-bit, you might have better luck.

---

