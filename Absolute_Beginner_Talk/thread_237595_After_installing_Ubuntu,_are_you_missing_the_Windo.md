---
title: "After installing Ubuntu, are you missing the Windows boot option?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by daou on 2006-08-16
I thought I would share something that I had some trouble with and caused me multiple (unnecessary) installations.

If, after installing Ubuntu (or after just reinstalling grub), grub doesn't have an option to boot an existing WinXP installation or the current one doesn't work, you can always add (or edit) the option to the grub menu in Ubuntu.

To do this, something like the following has to be appended to the end of **/boot/grub/menu.lst** file, right above the "### END DEBIAN AUTOMAGIC KERNELS LIST" line:

```
title	Windows XP
rootnoverify	(hd1,0)
map 		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
makeactive
boot
```

This is from my menu.lst. What it says is to look for WinXP in the first partition in the second hard drive (the order of which is defined in BIOS).

(hd#,#) = (hard drive number, partition number)
and
(hd#) = hard drive number
first # being 0

Then it makes a virtual map that fools WinXP into thinking its located on the primary hard drive. This has to do with WinXP refusing to boot unless it's located on the first hard drive in the boot sequence. 

To make it work on your platform, 
replace (hd1,0) and the (hd1) with whatever hdd and partition your WinXP is located in.
If your Windows is located on the first hard drive (hd0), then both the map options can be omitted.
If you don't get it right the first time (for example using the wrong harddrive or partition number), you can always edit the boot options during boot in grub by pressing 'e' after highlighting the WinXP boot option. All changes made during boot are temporary and will be cleared next time you boot so no worries. Just remember to update the menu.lst file with the correct info next time you are in Ubuntu so you won't have to edit the options every time you boot.

---

### Post by Klaidas on 2006-08-16
You could post this a howto in howto section (or ask a mod to move it there):  [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100) :)

---

### Post by gusarapez on 2006-08-16
Thanks a lot for the information.

I was having exactly the same problems and your tip worked perfectly.

---

### Post by daou on 2006-08-16
>  You could post this a howto in howto section (or ask a mod to move it there):

Good call.

> Thanks a lot for the information.

I was having exactly the same problems and your tip worked perfectly.

Glad it helped. No reason to reinvent the wheel.

---

