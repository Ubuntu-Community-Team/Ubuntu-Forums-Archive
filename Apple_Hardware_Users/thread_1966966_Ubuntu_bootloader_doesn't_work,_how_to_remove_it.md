---
title: "Ubuntu bootloader doesn't work, how to remove it?"
date: 2012-04-27
forum: Apple Hardware Users
---

### Post by bravegag on 2012-04-27
Hello,

I have a MBP 17'' mid 2009 version 5,2

I managed to install Ubuntu latest 12.04 Desktop in dual boot.

The Ubuntu bootloader doesn't work, I can choose and enter only to Ubuntu but not to Mac OS X. My only way to get to Mac OS X is to use the Opt key on startup and choose Mac OS X. 

What I would like ideally to do is:
1) get rid of Ubuntu bootloader altogether without breaking my MBR and system 
2) Have Mac OS X the boot disk by default and then if I want to login into Ubuntu I can use the Opt key upon startup.

Is there a way to do this risk free? 

TIA,
Best regards,
Giovanni

---

### Post by Kallun on 2012-04-28
Hi Giovanni,

Under OS X, install rEFIt (Google it). It's a common misconception that it's a boot loader, however it is in fact an EFI application, a graphical boot manager.

So upon booting up you'll be presented with a GUI which provides you the option to boot into OS X or Ubuntu (and any other operating systems you have installed).

It's very nifty and quite configurable! :)

You should be able to configure rEFIt in such a way it will behave close to what you want as you've described above. Basically, in the conf file, you could set the default timeout to 1 second, that way, when you turn on your MacBook, it'll wait one second for any intervention, then boot into OS X, however if you want to boot into Ubuntu, all you have to do is press the power button, then keep pressing/hold down one of the arrow keys, this will interrupt rEFIt's autoboot and allow you to select Ubuntu.

You won't be able to get rid of GRUB (Ubuntu's default boot loader) all together, as you have to chainload it from rEFIt, as I previously stated, rEFIt is not a boot loader.

It's super easy to get set up, just read the documentation on the site and feel free to ask any questions :)

---

### Post by bravegag on 2012-04-28
Hello Kallun,

Thank you for your detailed answer, I was actually trying to avoid rEFIt but is ok now it works very nicely.

Best regards,
Giovanni

---

