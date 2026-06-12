---
title: "Adding Windows XP to Grub2???"
date: 2012-02-16
forum: Any Other OS
---

### Post by apple_head on 2012-02-16
Hi everyone

I've recently created a multi boot system with Windows XP on the first partition of my SATA hard disk (sda1) and have Linux Mint on the second partition (sda2) and Windows 8 DVP on a slave IDE (sdb)

I installed both Windows operating systems first and then Mint last, however Grub2 does not pick up XP? And picks up Windows 8 as "Windows Recovery Environment?" 

How do I go about adding in Windows XP and changing the names of the entries?

I could do it on Grub Legacy but haven't a clue on Grub2?

---

### Post by darkod on 2012-02-16
This is no fault of grub. When you install more than one MS OS, it combines the boot files together. That's why grub detects only one set of boot files and creates only one entry in the boot menu.
When you select it, the windows bootloader should offer you options for both windows OSs.

As for the name, win8 is still too new and I guess it detects it as recovery environment. The title is just a title, there should be no problem what ever it's called.

---

### Post by oldfred on 2012-02-16
I do not use grub customizer, but I think it can change the name. Or you can do it manually with some of the guides drs305 has posted.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 wrote a Grub 2 Tweaks guide but it's pretty geeky stuff. If you are interested in editing the Grub2 scripts to rename a title, see Section 7 of the "Tweaks" link 
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

