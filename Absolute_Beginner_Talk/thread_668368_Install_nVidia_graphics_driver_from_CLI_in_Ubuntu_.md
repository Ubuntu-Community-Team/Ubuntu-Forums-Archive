---
title: "Install nVidia graphics driver from CLI in Ubuntu HH"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by stargazy on 2008-01-15
I've just upgraded my video card from nVidia 6150LE (integrated graphics) to nVidia 6600GT.  I run a dual boot system with Windows XP and Ubuntu ("Hoary Hedgehog").  New card is working nicely in Windows, but booting into Unbuntu is a problem--cannot boot reliably except in Safe Mode.  Also, X is not working.  I am able to edit /etc/X11/xorg.conf (but haven't, since I don't know what changes to make).   Would editing this file correctly solve my problem?  Do I have to download the nVidia driver file?

Thanks,
Grandma

---

### Post by phidia on 2008-01-15
You can change the xorg.conf file to the "nv" open source driver and then when you restart x and have a gui again use synaptic to reinstall your driver. I think that's the approved method.
Later versions of Ubuntu allow you to installed the nvidia driver from System>Administration>Restricted Drivers.

If your internet connection is up in CLI you could use apt to re-install the nvidia driver too. 
Check the multimedia and video forum [here]("http://ubuntuforums.org/showthread.php?t=301499") for more details.

---

### Post by Majorix on 2008-01-15
I thought you were referring to Hardy Heron with your HH when I first saw it.

Hoary Hedgehog is a really old distro. You could consider upgrading to Feisty Fawn or Gutsy Gibbon (preferred).

---

### Post by stargazy on 2008-01-15
You're right! I guess the name Hoary Hedgehog really stuck with me.  I am running "Gutsy Gibbon".

Love those names!

Grandma

---

