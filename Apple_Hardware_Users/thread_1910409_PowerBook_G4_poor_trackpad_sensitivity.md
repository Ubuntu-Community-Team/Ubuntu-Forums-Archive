---
title: "PowerBook G4 poor trackpad sensitivity"
date: 2012-01-17
forum: Apple Hardware Users
---

### Post by gwjvan on 2012-01-17
Hey,

I've installed Ubuntu 11.10 on my  PowerBook G4 1.67ghz 15" (PowerBook5,8 ) and the trackpad has poor sensitivity/response with slow finger movement. For example, when I lightly move my finger the cursor initially stays put, then all-of-the-sudden starts a second later. It will not initially respond to an X direction movement if I'm going in the Y, and vice versa. (A weird effect of this is that the cursor will move in a square formation on screen if I lightly make a circular gesture on the trackpad). Fast movements work fine. But anything requiring precision (selecting text, a particular small pixel range, or even just hitting a menu item) becomes very difficult. I'm able to slowly move my finger all the way across the trackpad without the cursor moving at all, at times.

The trackpad works great in OS X (not a hardware issue), and an external USB mouse plugged into the computer works great. I'd love to use the trackpad, however. So much else on the computer has worked great in Ubuntu (thank you for all of the  FAQ's, and ground-work getting it up and running, everyone).

I've played with xorg.conf (and none of the settings I've changed seemed to do anything). Does anyone have experience with this particular machine running Ubuntu? (I installed 10.04 first, then did an upgrade path to 11.10, if that sheds any light on the issue... it was the only way I could get any ubuntu installed on it at the moment)

---

### Post by rsavage on 2012-01-17
Sorry, can't help you with this one.  I can only point you in the direction of links you have probably already seen: [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) and [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) .
 
There have been a lot of changes with input devices and xorg.conf etc ([https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick](https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick) ) so maybe that is why your changes are not having any effect?
 
Have you tried the program Gsynaptics?  Maybe turn off multitouch stuff if it is turned on?
 
Maybe ask in one of the other forums if you don't get another reply here?
 
If you find out an answer then please add it to the PowerPC FAQ wiki.  Thanks.

---

### Post by gwjvan on 2012-05-26
Update:

Turns out the issue is with the appletouch driver. Late PowerBooks and Early MacBooks use this driver, and it has sensitivity settings which are defined in the source file, appletouch.c.

There's more information about this problem, here:

[http://ubuntuforums.org/showthread.php?t=813884](http://ubuntuforums.org/showthread.php?t=813884)

including a quick fix (when compiling the driver) to the sensitivity settings that made the touchpad usable. I'm looking into improving the driver or at least tweak it some more. I'll post more on that thread as I have more information

---

### Post by rsavage on 2012-05-26
qwjvan, can you update the FAQ with any necessary links/instructions?  Thanks
 
Btw, have you had a look at appletouch.txt in the documentation directory of the kernel source?

---

### Post by gwjvan on 2012-05-26
Sure- I've reinstalled ubuntu and I'm going to write down the steps I took to compile the driver. As far as appletouch.txt goes: it doesn't seem to address this issue directly

Also, would it be okay for me to post my modified driver? I can't compile a driver for intel MacBooks  (I don't have one), but at least if someone else has my model they can just download my appletouch.ko and save some trouble.

I'll update the powerpc faq- I should have more info soon (probably in the other thread or ppc faq, for anyone else looking for info)


Here's the post which explains how to compile appletouch:

[http://ubuntuforums.org/showthread.php?p=11973897#post11973897](http://ubuntuforums.org/showthread.php?p=11973897#post11973897)

---

