---
title: "Broke X during dist-upgrade. Need help."
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by Zeroangel on 2006-03-16
Hi everyone,

I somehow managed to break X during a dist-upgrade (viewing this in Lynx right now). And I would like your guidance.

First of all when I try to boot up, ubuntu loads the 2.12 kernel (not the recent 2.15 kernel), and then for a while I get the ubuntu boot splash then about 6 operations in, it switches over to plain text bootup. And I get a message stating that X and GDM cannot start, would I like to view the output... Y

Then a psuedo-window pops up designed to tell me what went wrong with X, however I cannot actually use the psuedo-window since in the middle of the screen a login prompt appears. The gist of this all is that I want to know how I can enable the 2.15 kernel in grub, and how I might provide you gurus with more useful information (things in logfiles, etc) with only access to the console/lynx.

Thanks in advance,

---

### Post by taurus on 2006-03-16
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Zeroangel on 2006-03-16
OK, I'm looking at my /var/log/Xorg.0.log file (and hoping this info will be useful) and I can see the following errors:

- Missing font directories (/usr/share/X11/fonts/cyrillic and /usr/share/X11/fonts/CID). Entries deleted from font paths.
- fonts.dir not found in "var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
- Then there is a bunch of hex matrices regarding my video card (GeForce4-MX400)
- Then I get some error messages about X being unable to load libGLcore and GLcore files
- More modules load (OK)
- Towards the end of the file I get an error message that X cannot load module "nvidia" (module does not exist)

---

### Post by taurus on 2006-03-16
Oh.  Then you need to edit your /etc/X11/xorg.conf and change the driver for your video card "nvidia" back to "nv" or even "vesa"...
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by Zeroangel on 2006-03-16
[QUOTE=taurus]```

sudo dpkg-reconfigure xserver-xorg

```[/QUOTE]
Thanks!

It seems that xserver-xorg wasn't even installed properly. So i'm reinstalling it right now from apt-get. I will post any further devleopments.

---

### Post by taurus on 2006-03-16
Good luck, dude.

---

### Post by Zeroangel on 2006-03-16
[QUOTE=taurus]Oh.  Then you need to edit your /etc/X11/xorg.conf and change the driver for your video card "nvidia" back to "nv" or even "vesa"...
```

sudo nano /etc/X11/xorg.conf

```[/QUOTE]
Setting my driver back to "nv" is the last thing that fixed X. Everything works great now. :KS 

Thanks for your help.

(OMG, Nautilus is so fast now)

---

### Post by taurus on 2006-03-16
[QUOTE=Zeroangel]
(OMG, Nautilus is so fast now)[/QUOTE]
I guess you have a fast machine with plenty of RAM then!  :)

---

