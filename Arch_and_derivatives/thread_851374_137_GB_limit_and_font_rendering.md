---
title: "137 GB limit and font rendering"
date: 2008-07-06
forum: Arch and derivatives
---

### Post by Average Joe on 2008-07-06
I have been wanting to use Arch as my main distro for a while now. I like the idea of having clean configuration files and the rolling release.

Two things are keeping me back from switching:

1) The 137 GB limit. My bios (Acer laptop) does not support hard disks larger than 137 GB. Ubuntu has never had a problem with that. It just overrules whatever is in the bios and sees my whole 160 GB disk. Arch doesn't. With the older releases of Arch I could use the 'ide-legacy' boot option and it would work (although I would end up with hdx devices instead of sdx). However, with the latest release (2008-06) this doesn't work any longer. Beats my why, and I don't like the idea of first installing an older version and then upgrade. After all, the whole idea of a rolling release is that it shouldn't matter what release you start with, right? But apparently it does.

2) The font rendering. I like the Ubuntu font rendering. I simply cannot get it the same with Arch. On both I use Gnome, and I use the same font rendering settings. I even copied the entire /etc/fonts directory from my Ubuntu partition to the Arch partition. No dice. With Arch the fonts are not quite as neat as with Ubuntu.

Does anybody have experienced similar problems, or knows a way to solve (one of) them?

---

### Post by fwojciec on 2008-07-06
re 2:  There are at least two sets of packages that alter font rendering and make it ubuntu like (i.e. enables sub-pixel font smoothing) available in AUR: see for example fontconfig-lcd, cairo-lcd, and libxft-lcd.  There was also a set of "*.-ubuntu" packages, but I'm not sure if these are still available.

---

### Post by MisfitI38 on 2008-07-06
> **Average Joe said:**
> 
1) The 137 GB limit. My bios (Acer laptop) does not support hard disks larger than 137 GB. Ubuntu has never had a problem with that. It just overrules whatever is in the bios and sees my whole 160 GB disk. Arch doesn't. With the older releases of Arch I could use the 'ide-legacy' boot option and it would work (although I would end up with hdx devices instead of sdx). However, with the latest release (2008-06) this doesn't work any longer. Beats my why, and I don't like the idea of first installing an older version and then upgrade. After all, the whole idea of a rolling release is that it shouldn't matter what release you start with, right? But apparently it does.



Just figure out what the kernel argument was and append it to the end of the kernel line on the new ISO. 
Something like ide=generic or something

---

### Post by Average Joe on 2008-07-06
Thanks for your answers, guys! I will try your solutions.

fwojciec, I remember I have been trying to fiddle around a bit with some 'cairo' package. I couldn't get it to work then. Maybe I should try again (and a bit harder).

MisfitI38, I have been trying to find out what boot-options are available. I could only find the ones mentioned in the Arch Wiki. So I actually wouldn't know how to "Just figure out what the kernel argument was". I find it strange that the boot option 'ide-legacy' used to work for me, and now it doesn't any longer. Would that be because of a change in the kernel, or because of a change how the boot-option is handled?

---

### Post by fwojciec on 2008-07-06
Here's a wiki page that might be useful for the fonts issue: [http://wiki.archlinux.org/index.php/Fonts#.22LCD.22_packages]("http://wiki.archlinux.org/index.php/Fonts#.22LCD.22_packages")

---

### Post by MisfitI38 on 2008-07-06
> **Average Joe said:**
> Thanks for your answers, guys! I will try your solutions.

fwojciec, I remember I have been trying to fiddle around a bit with some 'cairo' package. I couldn't get it to work then. Maybe I should try again (and a bit harder).

MisfitI38, I have been trying to find out what boot-options are available. I could only find the ones mentioned in the Arch Wiki. So I actually wouldn't know how to "Just figure out what the kernel argument was". I find it strange that the boot option 'ide-legacy' used to work for me, and now it doesn't any longer. Would that be because of a change in the kernel, or because of a change how the boot-option is handled?

Boot with the OLD iso, then hit 'e' at the grub prompt for ide-legacy. Scroll to the end of the kernel line and see what the kernel argument is.
Do the same thing with the new iso and append the argument. (If the kernel arguments are identical, then I suppose it is a kernel version issue.) :)

---

### Post by Average Joe on 2008-07-07
Thank you both again.

fwojciec, I have been googling for some font rendering things, but I don't think I have come cross that part of the Wiki page before. Stupid of course, that should be the first place to check. Anyway, I will try it out.

MisfitI38, that seem to be the right solution. Although I find it strange that they would change the kernel-arguments, and not change the name of the boot-option. Plus, I wonder if that stuff is not documented somewhere. But I will try it out too.

It might take a while though. I hosed my Arch installation because I wanted to try OpenSUSE (didn't like it too much). Plus, I have overwritten my old Arch iso cd with the new iso...

---

### Post by Average Joe on 2008-07-09
**Update:**

MisfitI38, There is no grub prompt with the old (2008-03) Arch iso, so I couldn't check for any kernel arguments. But anyway, I used this iso to install Arch with the ide-legacy boot option. My full hard disk (160 GB) was recognized. I just updated my system afterwards. I still don't know why the ide-lecagy boot option doesn't work for me with the new iso (2008-06).

fwojciec, I used the (now deprecated!) instructions to get my fonts better. I was not entirely impressed. But after I installed the deja-vu font (pacman -S ttf-dejavu) things look much better now. I need to check whether this is just because of the font only, or if I still need the lcd stuff in your instructions as well.

Happy Joe :)

---

### Post by ruffEdgz on 2008-07-11
If you are looking for a good font, my friend shared with me ttf-liberation and I love it a lot.

I would still try what fwojciec suggested about the lcd fonts but just another thought of a good font I use :D

---

### Post by mips on 2008-07-12
also try bitstream vera sans font.

---

