---
title: "Snow Leopard dualboot Ubuntu 12.04 (grub and rEFInd)"
date: 2014-03-14
forum: Apple Hardware Users
---

### Post by a1492dc on 2014-03-14
Hello,

After installed rEFInd I have installed Ubuntu 12.04 on my Macbook 4-1 which runs Snow Leopard 10.6.

Now on startup I have GRUB instead of rEFInd and even if it shows Mac OS X, an error outcome if I try to run it.

If I exit from GRUB, rEFInd appears and I can lunch both operating system.

So I would like to fix GRUB in order to lunch Mac OS X from there, or deactivate GRUB and lunch rEFInd on startup.

Someone can help me?

Thanks

---

### Post by este.el.paz on 2014-03-14
> **a1492dc said:**
> Hello,

After installed rEFInd I have installed Ubuntu 12.04 on my Macbook 4-1 which runs Snow Leopard 10.6.

Now on startup I have GRUB instead of rEFInd and even if it shows Mac OS X, an error outcome if I try to run it.

If I exit from GRUB, rEFInd appears and I can lunch both operating system.

So I would like to fix GRUB in order to lunch Mac OS X from there, or deactivate GRUB and lunch rEFInd on startup.

Someone can help me?

Thanks

It's hard to know exactly why what you are experiencing is happening . . . or the details of what is happening are not clear.  I have done the same more or less, except I have triple boot, for two flavors of OSX, and one flavor of Linux Mint . . . .   The details of how you did your installs might be helpful to know; but rEFInd should be installed from the Sno Lep system . . . so it gets put in front of the OSX partition . . . and then the 'Buntu system gets installed after that, with GRUB being set up in front of the linux system.  OSX doesn't play well with other systems, so for instance, if you installed linux first, and then installed osx, no, that probably won't work out.

rEFInd is pretty good . . . but there might be some other things to install via the terminal to get it to work, you have to read the instructions to install it very carefully . . . .  In my triple boot set up I have 10.6.8 as the "native" system and I installed rEFInd in front of the 10.8.2?? partition, so, if I cold start the computer opens with 10.6.8 without doing anything; if I want linux or 10.8.2 I have to hold the "option" key down on reboot and that takes me to the OSX boot manager window?? that shows the 4 hadr disk images . . . and if I hit Macintosh2 it will take me to the rEFInd window, where I can choose any of them there OR also in the boot manager window is showing "Windows" disk and if I click there it goes to the GRUB window . . . and then to the linux gdm log in window.  It's a bit more complicated when doing the dual boot or triple boot set up . . . but once it's done, it's easy.  

So, uh, somewhere along the install process . . . there was a mistake . . . .  : - ))  One other option, for 10.6.8 you could use rEFIt . . . and that ***might**** be easier to get it to work, following the online instructions; the only problem with that app is it doesn't work for newer systems than 10.6.8 and that's why I switched to rEFInd . . . .

e.e.p.

---

