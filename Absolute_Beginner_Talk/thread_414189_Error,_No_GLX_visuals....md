---
title: "Error, No GLX visuals..."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by plinny on 2007-04-19
Hello all! 
        I'm a noob at all this stuff, and bit off more than I can chew.  I  was trying to install Xgl (to install Beryl), and messed with BOTH my xorg.conf, and my gmd.conf-custom.  I have since reconfigured them both, but still I get no graphics!!!:((   I'm running an e-machine laptop, AMD Athlon with an Intell i810 graphics card.  I can't seem to figure a way to get the error info to show ya'll (I'm using a diff. computer now).  The one error I keep getting is that there is no GLX visuals....any help??
         Thanks a bunch!
                 plinny

---

### Post by leibowitz on 2007-04-29
First thing to fix is your **/etc/X11/xorg.conf** file.

Please post it here.

You may need to uninstall some packages aswell.

But try to reconfigure your xorg.conf with the dpkg-reconfigure command.
```

sudo dpkg-reconfigure xserver-xorg

```

Post your **/var/log/Xorg.0.log** too

---

