---
title: "Impossible to boot 11.04 live cd on a Mac Pro"
date: 2011-05-08
forum: Apple Hardware Users
---

### Post by LaurentR2D2 on 2011-05-08
Hello,

I try to run the live cd of Ubuntu 11.04 on a Mac Pro 2006 / Snow Leopard which is connected to a Cinema Display 24 "mini display. I get a first display with text commands, then a splash screen indicating the launch of the live cd, and nothing more.The live cd hangs on a black screen. Is this related to an incompatibility with the Mac Pro or mini display port? Yet I get the first part of the launch. I've tried the live CD successfully on a Macbook Pro.

Thank you

---

### Post by samuaz on 2011-05-08
try tis the mac iso (64-bit Mac (AMD64) alternate install CD) in this link [http://cdimage.ubuntu.com/releases/natty/release/](http://cdimage.ubuntu.com/releases/natty/release/)

---

### Post by DoubleClicker on 2011-05-09
At the boot menu screen, hit F6, then select nomodeset, and hit escape.  You will see a grub command line appear.  Forsome reason the nomodeset doesn't appear in the command line, so move the cursor to just before **quiet splash** and type **nomodeset xforcevesa**.  Then hit F10 to boot. 

You will only have vesa graphics, but you will be able to install.

---

### Post by LaurentR2D2 on 2011-05-09
> **DoubleClicker said:**
> At the boot menu screen, hit F6, then select nomodeset, and hit escape.  You will see a grub command line appear.  Forsome reason the nomodeset doesn't appear in the command line, so move the cursor to just before **quiet splash** and type **nomodeset xforcevesa**.  Then hit F10 to boot. 

You will only have vesa graphics, but you will be able to install.

Thank you. It has worked fine. The only difference is that I've hitten Enter instead of F10 since F10 was offering me to shut down my machine.

---

### Post by DoubleClicker on 2011-05-11
> **LaurentR2D2 said:**
> Thank you. It has worked fine. The only difference is that I've hitten Enter instead of F10 since F10 was offering me to shut down my machine.
You are right, I was confusing it with the installed grub.  After installation, you still need to do this from grub, if you haven't installed the proprietary (fglrx) driver.

---

### Post by konnichwakid on 2011-05-20
> **DoubleClicker said:**
> At the boot menu screen, hit F6, then select nomodeset, and hit escape.  You will see a grub command line appear.  Forsome reason the nomodeset doesn't appear in the command line, so move the cursor to just before **quiet splash** and type **nomodeset xforcevesa**.  Then hit F10 to boot. 

You will only have vesa graphics, but you will be able to install.


Just to add clarification and since it caused me to pause for a bit, hit F6 on the screen after you have selected your language. In other words the boot menu screen appears after you select your language. Thanks!

---

### Post by konnichwakid on 2011-05-24
> **DoubleClicker said:**
> You are right, I was confusing it with the installed grub.  After installation, you still need to do this from grub, if you haven't installed the proprietary (fglrx) driver.

Wait, so the instruction got everything installed, but then when it reboots it stops on a screen with some text but no way to get around it. It looks like it is still booting with the Mac booter. How do I change grub or what should I do now?

---

