---
title: "[SOLVED] cant make compiz fusion enable"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by astathios on 2008-01-13
hello i need some help , i use a fujitsu siemens laptop with an ati x1400 and i cant make compiz enable.
this is the report of the teminal

stathis@stathis-laptop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

i dont want to download xgl cause last time i did my system crashed
any other help would be apreciated
thanks in advance

---

### Post by Sef on 2008-01-13
You need the restricted drivers to make Compiz-Fusion work.  (System > Administration > Restricted Drivers Management.)  Without them, you can't use C-F.

---

### Post by dustman on 2008-01-13
hello!

in my search to install compiz fusion (with which i also has problems) i found these HOW-TO's, which worked flawlessly for me :

- for Gutsy Gibbon:   [http://ubuntuforums.org/showthread.php?t=580748&highlight=gutsy+gibbon](http://ubuntuforums.org/showthread.php?t=580748&highlight=gutsy+gibbon)


- for Feisty Fawn: [http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html)

Hope it helps!


Radu

---

### Post by astathios on 2008-01-13
i deicide to install xgl 
so i got a result and i made all the necesary from synaptic
but i got this in terminal

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Error: Can't load plugin 'imgjpeg' because it is b
uilt for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'imgjpeg'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'text' because it is buil
t for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'text'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'neg' because it is built                                                                             for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'neg'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12                                                                             image format
/usr/bin/compiz.real (core) - Error: Can't load plugin 'wall' because it is buil                                                                            t for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'wall'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'snap' because it is buil                                                                            t for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'snap'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'animation' because it is                                                                             built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'animation'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'expo' because it is buil                                                                            t for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'expo'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'resizeinfo' because it i                                                                            s built for ABI version 20070606 and actual version is 20070915
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'resizeinfo'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'workarounds'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ezoom'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'vpswitch'

---

### Post by dustman on 2008-01-13
did you enable the restricted drivers for your video card? : System->Administration->Restricted Drivers Manager. This is in GNOME. If you have KDE, there must be some tutorial on how to make compiz work. And i think you have to remove all the stuff you have previously installed (like it's stated there in those HOW-TO's i posted)


Radu

---

### Post by pizzavortex on 2008-01-13
I have a similar problem.  I have a dell pc with an ati radeon x1300. I have all the necessary drivers.  I got compiz to work by installing xserver-xgl but 3d graphics accelleration stopped working so i couldn't play any games.  I only really want the emerald window decorator.  if there is a way to get compiz to work without xgl or my games to work with xlg or a way to use emerald without compiz, could you please give me a hint?

---

### Post by astathios on 2008-01-13
> **dustman said:**
> did you enable the restricted drivers for your video card? : System->Administration->Restricted Drivers Manager. This is in GNOME. If you have KDE, there must be some tutorial on how to make compiz work. And i think you have to remove all the stuff you have previously installed (like it's stated there in those HOW-TO's i posted)


Radu

i have gnome the restricted drivers are enable.
the problem half solved with the xgl update but still....

---

### Post by astathios on 2008-01-13
oopps
it worked i just had to reinstall from synaptic. I guess the problem was the xgl 
tnanx

---

### Post by dustman on 2008-01-13
> **astathios said:**
> i have gnome the restricted drivers are enable.
the problem half solved with the xgl update but still....

i still think that you haven't removed all of the previous installation. Found this post that confirms this: [http://ubuntuforums.org/archive/index.php/t-597726.html](http://ubuntuforums.org/archive/index.php/t-597726.html) . 
Like it's stated there, open up a terminal, then enter: 
```
sudo apt-get remove compiz* libcompiz* emerald libemerald*
```

After that, use the instructions from the links i posted earlier. It has to work.

---

### Post by dustman on 2008-01-13
great ! have fun :)

Radu

---

