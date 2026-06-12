---
title: "vista + ubuntu"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sameer.india on 2008-04-10
I have dual boot but widows has some problem and I wish to reinstall it but when i have done it before ubuntu was uninstalled. I don't wish that to happen.

---

### Post by jesusfreak107 on 2008-04-10
> **sameer.india said:**
> I have dual boot but widows has some problem and I wish to reinstall it but when i have done it before ubuntu was uninstalled. I don't wish that to happen.
Ubuntu was most likely not installed, the GRUB was merely written over by Window's MBR.  Install GRUB on your Windows, after you have installed it, and you will be able to boot into either one.  As long as you don't format that drive during installation.  oh, and, get XP.  Vista is horrible, and buggy, and VERY VERY VERY resource-consuming.  without doing anything, it takes up over 700MB RAM.  And, changing the look to Windows Classic style, takes away a full 300MB of that.   It is a VERY bloated OS.  XP is good, and stable.

---

### Post by ibutho on 2008-04-10
Ubuntu wasn't uninstalled. Vista probably overwrote the MBR wiping off grub so you could not boot into Ubuntu. If this happens, one option is to use the [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to reinstall grub and you will be able to boot again into Ubuntu.

---

### Post by bodhi.zazen on 2008-04-10
It should be no problem.

Go ahead and re-install windows. DO NOT format or overwrite the Ubuntu partition(s).

Then restore grub (to allow dual booting)

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by sameer.india on 2008-04-10
well i have vista should that be a problem

---

### Post by bodhi.zazen on 2008-04-10
If it is currently dual booting without any problem, re-installing Vista should not be a problem.

---

### Post by lswest on 2008-04-10
Yeah, i have a link in my sig (second line) to a how-to i wrote on restoring bootloaders (XP's, Vista's and GRUB), why don't you have a look at it?

---

### Post by igknighted on 2008-04-10
> **jesusfreak107 said:**
> Ubuntu was most likely not installed, the GRUB was merely written over by Window's MBR.  Install GRUB on your Windows, after you have installed it, and you will be able to boot into either one.  As long as you don't format that drive during installation.  oh, and, get XP.  Vista is horrible, and buggy, and VERY VERY VERY resource-consuming.  without doing anything, it takes up over 700MB RAM.  And, changing the look to Windows Classic style, takes away a full 300MB of that.   It is a VERY bloated OS.  XP is good, and stable.

Good advice, but please keep the preaching to yourself, at least in the support forums.  Vista is a far more secure option in today's networked world than XP can ever dream to be, and who's to say the OP doesn't have 2+ gb of ram and not care about the initial footprint?  I can certainly understand not going out of your way to get Vista for a computer designed for XP, but I also cannot imagine why one would go out of his/her way to get XP on a computer designed for Vista.

---

### Post by sameer.india on 2008-04-10
Will this process in any way affect ubuntu

---

### Post by lswest on 2008-04-10
Nope, shouldn't at all.  Most that will happen is it will run an fsck after restoring GRUB to check for errors (if you mounted it in vista before hand). Also, thanks for the thanks ^^

---

### Post by bodhi.zazen on 2008-04-10
> **sameer.india said:**
> Will this process in any way affect ubuntu

It will overwrite grub in the MBR, which is why you need to restore it post-install.

The only way to otherwise affect Ubuntu would be if you formatted or installed windows on the Ubuntu partition, so be careful with the Vista install process.

---

