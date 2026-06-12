---
title: "Drivers for ATI Xpress 200"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Seriphyn on 2007-04-20
I'm on a laptop atm, and I see everyone is worried about installed X series cards, and the sticky seems to apply to that as well.

I've downloaded the drivers from the site, but Ubuntu can't seem to run '.run' files. However, there is a "Restricted Drivers" option in System. I run that, I see "ATI accelerated graphics driver", go "w00t!" and then tick it and apply.

Nothing happens. It is still "not in use". So, how on earth do I get my ATI Xpress 200 runnin' so I can play games like Vega Strike (or most desktop games for that matter) and use desktop effects? Thanks.

---

### Post by Seriphyn on 2007-04-20
bump.

---

### Post by Seisen on 2007-04-20
[http://ubuntuforums.org/showthread.php?p=1399268]("http://ubuntuforums.org/showthread.php?p=1399268")

---

### Post by lamalex on 2007-04-20
after you ticked it did you restart? that's the trick :)

---

### Post by feed_sparky on 2007-04-20
```
sudo apt-get update
```

put that in a terminal, and then try it. I have the same card and that's what I had to do before it would download the drivers.

---

### Post by Toadmund on 2007-04-20
I'll have to try this later on tonight, I concur with the original poster.
I'll report back if it works for me, hope it does, I've tried everything else.

---

### Post by Seriphyn on 2007-04-20
Ah yes, those instructions did apply for Xpress 200. After doing that, resetting, the restricted drivers manager came up and said that the ATI drivers were now "in use". Hoorah!

Uh oh!

Click on "Desktop effects". Comes up with, "The Composite extension is not available". What happened!!!???

Also, Chess says something about these OpenGL extensions. I think I might need those for other things too. Where can I find them? Desktop effects problem top priority though, thanks.

---

### Post by feed_sparky on 2007-04-20
> **Seriphyn said:**
> Ah yes, those instructions did apply for Xpress 200. After doing that, resetting, the restricted drivers manager came up and said that the ATI drivers were now "in use". Hoorah!

Uh oh!

Click on "Desktop effects". Comes up with, "The Composite extension is not available". What happened!!!???

Also, Chess says something about these OpenGL extensions. I think I might need those for other things too. Where can I find them? Desktop effects problem top priority though, thanks.

I get the same error message when I try to enable Desktop Effects, must be another ATI problem :( 

but here is a link that might help with XGL and Beryl [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

---

### Post by Seriphyn on 2007-04-20
Very nice dude. I'll try that. However, I'm wondering if my laptop will be able to handle Beryl with these specs...

Intel Celeron M 1.5ghz
512MB RAM
ATI Xpress 200M (as you know)

Also, will Beryl work well with games too? Such as Vega Strike? Can I easily switch Beryl on and off.

Thanks so much so far. It's been immense.

---

### Post by floke on 2007-04-20
Beryl's easy to switch on and off.
If you can get the ATI part working the rest of your specs seem ok to me (unless the 512 is shared memory, in which case things might get a bit bum-squeaky)

---

### Post by Seriphyn on 2007-04-20
Awesome! Thanks everybody! I'll give it a shot. If it messes up then, well, I'll come running back here for God-given guidance =P

Thanks again.

---

### Post by floke on 2007-04-20
Dont forget to BACK UP YOUR XORG.CONF FIRST!!!

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

(reverse file paths to restore)

Good luck!

---

### Post by Toadmund on 2007-04-20
And more of this ](*,)   , seems it has an issue with xorg 7.2 not being recognized
```
toad@toad-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
Password:
toad@toad-desktop:~$ cd ~/Desktop
toad@toad-desktop:~/Desktop$ chmod +x ati-driver-installer-8.35.5-x86.x86_64.runtoad@toad-desktop:~/Desktop$ ./ati-driver-installer-8.35.5-x86.x86_64.run
Created directory fglrx-install.hb8174
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.35.5.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.2.x 64-bit

Detected version of X does not have a matching 'x720_64a' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.hb8174
toad@toad-desktop:~/Desktop$ 
```

---

