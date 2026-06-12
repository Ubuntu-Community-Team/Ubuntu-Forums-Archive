---
title: "Can't get Grub to load Mac OS X Leopard"
date: 2009-05-06
forum: Apple Hardware Users
---

### Post by Watari on 2009-05-06
I know, I know. Why did I not read a guide and do it in a different matter?

The facts are:

OS X Leopard partition is there. I did not erase it. I have tried some old code being added at the end of the grub file and I get error 8 or 13 depending on which I use.

Can somebody help by pointing to the right code?

I checked using fdisk. I am quite certain it is on partition (hd0,1).


Would really appreciate some help.

---

### Post by cyberdork33 on 2009-05-06
why are you trying to use grub to load OS X? Hold ALT during startup and choose the OS X volume to boot from.

---

### Post by Watari on 2009-05-06
> **cyberdork33 said:**
> why are you trying to use grub to load OS X? Hold ALT during startup and choose the OS X volume to boot from.

That does not work. Do you mean hold alt as soon as the white Apple screen comes on? If so the keyboard does not start working until I am in Linux and holding it there fast when it starts did nothing. I just want grub to allow me the option to choose Mac OS X when I am booting.

---

### Post by CyanideSyntax on 2009-05-07
no, hes talking about holding alt directly from a cold boot.
that will kickstart apple's bootloader, which is in the machine's firmware. basicly damn-near undelelteable.


start holding down alt/option before you even turn it on, and power it up holding it.
you should get a grey screen with harddrive icons that you can boot from. choose the os x one.

hope it helps.

---

### Post by hanzomon4 on 2009-05-08
Strange the default should be to boot into os x... unless you blessed something

---

