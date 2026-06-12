---
title: "How do I install a GRUB loader background?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2006-07-13
How do I install a GRUB loader background screen? I have Ubuntu 6.06 and Windows XP as "Other OSes" and Kubuntu is listed as the primary OS. Oh, can I change the order they are listed in? I would like Ubuntu as the primary not Kubuntu. And one thing seems strange to me, the Ubuntu install is listed twice on the GRUB list. Can I delete one without harming the install?

---

### Post by bohboh on 2006-07-13
> **dragon1964m said:**
> How do I install a GRUB loader background screen?

[http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot](http://www.ubuntuforums.org/showthread.php?t=208855&highlight=gfxboot)

> **dragon1964m said:**
> I have Ubuntu 6.06 and Windows XP as "Other OSes" and Kubuntu is listed as the primary OS. Oh, can I change the order they are listed in? I would like Ubuntu as the primary not Kubuntu. And one thing seems strange to me, the Ubuntu install is listed twice on the GRUB list. Can I delete one without harming the install?

/boot/grub/menu.lst is where all this is managed. (Make a backup first) It is commented to help you make any changes. With regards to it listed twice, that normally means that you updated your kernel, but you can still boot under your previous version if the newer one breaks something. So IMO i would leave it in.

HTH

---

### Post by Malac on 2006-07-13
```
sudo gedit /boot/grub/menu.lst
```
Gets you into the menu file this is fairly well commented to aid with customisation.
You can comment out # any entry you want but I wouldn't recommend deleting them.
Check the description for each of the Ubuntu's, one may be the "recovery mode" entry. Do not alter/delete this, you may need it.
If one entry is:
*title        Ubuntu, kernel 2.6.15-**25**-386*
and another is :
*title        Ubuntu, kernel 2.6.15-**23**-386*

then the -***23*** one is a lower version so can be removed but that should be done from Synaptic.

I don't think you can get a background picture in GRUB as it uses text based coding video modes however the is an option:
# Pretty colours
#color cyan/blue white/blue
which you could try to jazz it up a bit.

---

### Post by Malac on 2006-07-13
I stand corrected about the graphics, thanks bohboh. :)

---

### Post by OpsVentus on 2006-07-13
You can change the colors.
This is done in GRUB's menu.lst, that's located at '/boot/grub/menu.lst'.
That's also where you can change the order in which the OS's apear in the menu. And you can even remove old Ubuntu installs without harming the install!

The reason there are multiple Ubuntu listed is becauss, we got an normal boot and a failsafe boot, and that for every kernel installed. When updating to a newer kernel the old one is kept in place just in case the new one gives you troeble.

You can check the online manual of GRUB ([http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)) on how to change the file.

Have fun,
Bart.

---

### Post by bohboh on 2006-07-13
The biggest problem with gfxboot isnt getting it working, is finding nice themes! :D

---

