---
title: "Picture messed up using live cd"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Krii on 2007-01-03
I'm using live cd to boot in, but after I hear the intro sound picture is completely messed up. i tried different resolutions but nothing changed. I have lcd display 1280x1024 and gf6600. I also tried crt its the same on both. What do I do to fix it?

---

### Post by taurus on 2007-01-03
Are you just checking out Ubuntu or are you planning to install it on your machine?

Try pressing <Ctrl><Alt>F2 to get to a console and reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, press <Alt>F7 to get back to Gnome.  You may have to press <Ctrl><Alt>Backspace to restart X again...

---

### Post by Krii on 2007-01-03
I was planning to just check it out but it is no problem to install it if that will fix the picture. Anyway thanks for the tips I'll try them and see if it works.

---

### Post by taurus on 2007-01-03
If you plan to install it on your machine, I recommend you go with the alternate CD.  It allows to you install it right away instead of trying to boot from the CD before you can click the install button...

Don't forget to burn it at a slow speed like 4x!

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by Krii on 2007-01-03
But if the picture is messed up now how can I be sure it will be ok after I install it? And I checked x setting there are 3 lowest resolutions checked but if I change something the picture is still messed up so it doesnt help :-?

---

### Post by taurus on 2007-01-03
Once you've installed it, you can configure it easier and as far as I know, you shouldn't have problem running X since I have both GeForce 5700 and GeForce 6800 and alternate CD configured everything right out of a box.  Just have to install nvidia driver later to get some real 3D thing going...

---

### Post by Krii on 2007-01-03
I dont know... I would still prefer to fix this on live cd before installing it on my system. Maybe there is some way I can download and install drivers using live cd? O and using console only because I cant see anything else.

---

### Post by Krii on 2007-01-03
Any more ideas on how to fox this?... anyone?:-?

---

### Post by bodhi.zazen on 2007-01-03
> **Krii said:**
> Any more ideas on how to fox this?... anyone?:-?

Yes, but you will need to follow the advice of taurus :p

You can not install the nvidia drivers with the Live CD because they require a re-boot.

If you want to mess with xorg.conf (on the love CD) you can try the vesa driver ....

> Section "Device"
Identifier "twinview"
VideoRam 256000
VendorName "nVidia Corporation"
BoardName "Video device"
**Driver "nvidia"**

Change Driver 'nvidia' to ```
Driver "vesa"
```

This change may or may not give you a better temporary resolution until you install the nvidia driver.

---

