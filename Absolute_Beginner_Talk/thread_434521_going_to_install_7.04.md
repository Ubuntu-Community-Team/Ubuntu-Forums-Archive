---
title: "going to install 7.04"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by stalkingwolf on 2007-05-06
I have 4 computers, 2 desktops( one is a 6yr old Nutrend the other a 2 yr old GQ (frys store brand) and 2 laptops ( 1 EVO N410c, the other a Toshiba Techra),  All four are dual booted XP and Linux ( nutrend - linspire 5.*, GQ xandros, lap tops both have xubuntu 6.06)

Now the question.  Will I need to remove the current grub loader before I install the new Ubuntu?

If so what is the best way to do it?

---

### Post by Martje_001 on 2007-05-06
No, it will automatically be reinstalled. :D

---

### Post by HereInOz on 2007-05-06
I take it you are doing an upgrade, rather than a clean install?  In that case, should be no problems, but back up all your data just in case the unthinkable happens.

If you are doing a clean install, then, if your data is on the same partition as the Ubuntu system, be aware that you will lose it, so that is a compulsory backup!

---

### Post by Tundro Walker on 2007-05-06
Ubuntu will reinstall GRUB, and while it does a pretty good job of detecting Windows OS' to add to the boot list, I don't think it plays nice with other Linux installs.  So, if you wanted to tri-boot a system, say Ubuntu, Xandros, Windows, I'd be worried that Xandros wouldn't get detected.

However, this is easy to rememdy (if you don't mind tweaking a config file).  Just use your Linux install to find the file...

```
/boot/grub/menu.lst
```

Copy that file to a disk or usb key before installing Ubuntu for a tri-boot.  After installing Ubuntu, reboot, and more than likely you'll only get to choose from Ubuntu and Windows.  Remedy this by opening up that backup "menu.lst" file you copied.  Copy the "Xandros" lines from the boot list (should toward the bottom of the file), and paste them into the new, real "/boot/grub/menu.lst" file Ubuntu created, basically inserting Xandros as a boot option back into your list.

I used this method to get my old computer to tri-boot Windows, Ubuntu and Damn Small Linux (DSL) when I was first messing around with Linux distros.

---

### Post by stalkingwolf on 2007-05-06
I forgot to mention it will be clean installs.  First will be to get rid of the flaky Linspire 5.0.
Until it went flaky it did serve its purpose.  It worked well to introduce my computer challenged wife to linux.


Another question.  I tried the 7.04 live CDs for all 3 *buntus on all four machines.  With the xubuntu
cd on 2 of the machines I loose the top and bottom task bars,  the techra/ 14" display,  and the NuTrend/15"
display.  The other 2 GQ/19" display and Evo/ 13" display are fine with task bars and everything.  The screen
resolution is the same on all 4.  Any ideas?

---

### Post by Sef on 2007-05-06
> I forgot to mention it will be a clean install.

A clean install is best.  Less likely to have problems than doing an upgrade.

---

### Post by stalkingwolf on 2007-05-08
So does anyone have any ideas about the display question?


Another question. I tried the 7.04 live CDs for all 3 *buntus on all four machines. With the xubuntu
cd on 2 of the machines I loose the top and bottom task bars, the techra/ 14" display, and the NuTrend/15"
display. The other 2 GQ/19" display and Evo/ 13" display are fine with task bars and everything. The screen
resolution is the same on all 4. Any ideas?:-\"

---

