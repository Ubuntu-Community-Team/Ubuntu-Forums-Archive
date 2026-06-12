---
title: "[SOLVED] As Requested, my dell &amp;gt; acer problem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by lordofchaos1984 on 2007-11-12
i installed ubuntu on a 120gb HDD using my Dell Inspiron 1150, only because, for some reason the CD/DVD burner on my Acer Aspire 3000 isnt booting. I know that there is different hardware considerations, but i need to know how to get Ubuntu to put in the Acer crap into the install AFTER i move the HDD back. Thanks in advance.

Problem is that i had Freespire on an Acer Aspire 3000. Obviously Freespire crashed to the point that it could not get past 5 pixels on the loading bar. After much poking around, i decided that Ubuntu was in order. Now my Acer will not boot FROM CD/DVD and so i moved the HDD to my Dell Inspiron 1150. Install went off without a hitch but after i put the HDD back into the acer, it DOES give me a console login prompt, but i cannot get GDM to run. Do i need to edit the Xorg.conf file or is there an easy way to reconfigure X to work on the Acer?

---

### Post by cubeist on 2007-11-12
I assume the only problem here is that your xorg.conf file is tuned to the acer and you want it to recognize the other computer... or vice versa, your post is confusing... anyway, try this

sudo dpkg-reconfigure gdm

and if that doesn't fly, you could try editing your xorg.conf file by hand... or post it here an we will help

---

### Post by richiewrt on 2007-11-12
**edited** 
Im confused

---

### Post by qamelian on 2007-11-12
> **cubeist said:**
> I assume the only problem here is that your xorg.conf file is tuned to the acer and you want it to recognize the other computer... or vice versa, your post is confusing... anyway, try this

sudo dpkg-reconfigure gdm

and if that doesn't fly, you could try editing your xorg.conf file by hand... or post it here an we will help

That only reconfigure the Gnome Display Manager, not xorg.conf. For that, you need: ```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by lordofchaos1984 on 2007-11-12
thank you it has worked. did both reconfigures and it worked beautifully.

---

