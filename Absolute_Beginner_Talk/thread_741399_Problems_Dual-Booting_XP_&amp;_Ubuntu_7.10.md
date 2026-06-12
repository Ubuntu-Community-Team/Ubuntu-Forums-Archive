---
title: "Problems Dual-Booting XP &amp; Ubuntu 7.10"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by APSR on 2008-03-31
Hi, I'm new to Ubuntu... I'm having problems dual-booting ubuntu with xp. what happens is when the grub menu loads with all of the options  like ubuntu...etc windows xp home edt... I can't load XP once I install Ubuntu 7.10! it just gives a black screen and you have to hit the switch just to restart I have reformatted several times over the past few days and tried different partitions EXAMPLE: the default one that uses the free space... to the manual PATITION EDITS but it always ends with the same result:

 a blank screen when trying to load XP!

ALSO:

If I restore [non-destructive type of restore using recovery drive]  the Windows XP 
...I can't load Ubuntu!!! its a reversed effect! 
 It won't load ubuntu even with the super grub software thing I found while doing various searches on help!

anyone know what my possible problem could be?

here's the tech specs on my PC

emachines w3050... AMD SEMPRON 3000+....80GB HD...512MB

THANKS

---

### Post by Inxsible on 2008-03-31
are you sure you are not overwriting your xp partition during the ubuntu installation?

what partitioning method are you using? Guided partitioning? or manual ?

---

### Post by APSR on 2008-03-31
i'm not sure which one i used the first time i installed ubuntu but the last time [as mentioned above]  i used the manual,i setup its own patiton like an example i seen on another site showing how to setup patitons  as far as i can tell i didn't overwrite it however i've tried several different installations and ended up with the same result. the ubuntu will load but its a black screen when trying to load windows and vice-versa if i restore the windows without reformatting the harddrive. when i look into gparted it shows all of my patitions like the linux swap, the ntfs [windows] and the fat [the recovery for windows] i've already reformatted the disc twice and started from scratch each time i get the same results not sure why my system won't dual boot!

i'm currently dual-booting on my laptop that runs windows ME & Mepis 7.02 and it works fine Mepis won't run on this PC at all btw thats why i tried ubuntu! niether the 32 nor 64 bit edts will run on this pc of Mepis...not sure why but the disc won't even load just a grub comes up  and tells me to hit tab for options...

Ubuntu runs on this pc but it won't dual boot for whatever reason.

thanks

---

### Post by dstew on 2008-03-31
Boot a live CD. Does it mount your Ubuntu partition for you? That is, do you see the Ubuntu partition icon on the desktop? If so, go into the directory /boot/grub and post the contents of the menu.lst file. You can open it with a text editor, like gedit. Then, open a command line (Applications --> Accessories --> Terminal) and enter the command```
sudo fdisk -l
```Post the output of that command on the forum. We can compare the menu.lst contents with the fdisk output to see if the grub menu was set up properly during the Ubuntu installation. If not, maybe we can fix it.

---

