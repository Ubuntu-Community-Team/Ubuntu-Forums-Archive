---
title: "OSX BootLoader and Ubuntu"
date: 2016-01-08
forum: Apple Hardware Users
---

### Post by Foamy_Keiko on 2016-01-08
Forgive me if this has been asked before. I am new to Ubuntu. Proud to be using Ubuntu now. I have Ubuntu 14.04 installed and really want to keep my OS X Bootloader, which I currently have. A few things I'm trying to achieve:

Ubuntu is set as the default operating system to boot to, if I want to boot to OS X, I need to plug in a USB keyboard and hold Option (I'm using a 2013 iMac and have a Bluetooth Keyboard and Touchpad). Before my linux install if i wanted to bring up my boot menu my bluetooth keyboard was recognized and i could do so by pressing the Option key. Any ideas on how to get bluetooth to be recognized at this early stage again?

I'm also trying to get OS X back to my default operating system, and get an entry in my boot loader for Ubuntu, is this possible with Apples's boot loader?

---

### Post by este.el.paz on 2016-01-08
> **Foamy_Keiko said:**
> Forgive me if this has been asked before. I am new to Ubuntu. Proud to be using Ubuntu now. I have Ubuntu 14.04 installed and really want to keep my OS X Bootloader, which I currently have. A few things I'm trying to achieve:

Ubuntu is set as the default operating system to boot to, if I want to boot to OS X, I need to plug in a USB keyboard and hold Option (I'm using a 2013 iMac and have a Bluetooth Keyboard and Touchpad). Before my linux install if i wanted to bring up my boot menu my bluetooth keyboard was recognized and i could do so by pressing the Option key. Any ideas on how to get bluetooth to be recognized at this early stage again?

I'm also trying to get OS X back to my default operating system, and get an entry in my boot loader for Ubuntu, is this possible with Apples's boot loader?

@Foamy:

Apple bootloader doesn't go away . . . one way of doing what you are asking is that the next time you either upgrade OSX or do a Security Update, on restart OSX will set itself back as the default boot . . . that's probably the easiest.  I've been doing a few threads here, so I can't remember if you have rEFInd??  If you do the OSX upgrade/Security update, or, when you do, you would subsequently have to "re-bless" rEFInd to get its functions back . . . but, the apple bootloader will still show your choices . . . with the option key . . . possibly needing a non-bluetooth keyboard . . . .  

You probably could go into GRUB and select the "default" system . . . if that isn't obvious you can find and download "SuperGRUB2" repair disk . . . and I think that will give you a basic GUI to make adjustments to your GRUB settings . . . .  I tend to do a "hand's free" approach to using linux, not doing a lot of tweaking . . . because sometimes running "sudo apt-update" . . . and then "sudo apt-upgrade" will bring the fix you are looking for . . . .

Lastly, as linux is opensource . . . it doesn't do all of the bell's and whistles of OSX . . . the price for you may indeed be you need to "plug in" your keyboard . . . .  Question is whether OSX's open firmware accepts bluetooth inputs???

e...

---

