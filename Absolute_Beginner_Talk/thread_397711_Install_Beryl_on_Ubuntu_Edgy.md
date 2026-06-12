---
title: "Install Beryl on Ubuntu Edgy"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by MnInShdw on 2007-03-31
I've been on windows from win3.1
After years of using windows, I believe it's time to move to Linux.
I've installed Ubuntu Edgy and am trying to install Beryl on my system.

Here's my PC's spec
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Celeron(R) CPU 2.4GHz
768 MB RAM

I've searched every where on the net, but I wasn't able to find anywhere
with a installation tutorial for this purpose.
I followed the steps explained here
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
But it didn't work for me. I believe it's because of my graphics card is not ATI

How can I install Beryl on a PC with Intel Graphics card?

Thanks for any kind of help

---

### Post by Maestro23 on 2007-03-31
Good luck and welcome to Ubuntu: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by jordanmthomas on 2007-03-31
It's actually easier with an Intel card, as everything just seems to work without hassle.

Follow this:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

and this for your xorg.conf:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX)

Basically, all you need to fix in your xorg.conf is make sure this is at the end:
```
Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   Option "Composite" "Enable"
EndSection
```

and that in the Section labeled "ServerFlags"
you have this in it:
```
 Option     "AIGLX" "true

```

And finally, make sure you have these loaded in the "Modules" section near the top
```
    
    Load        "dbe"
    Load        "glx"
    Load        "dri

```
You'll surely have more, but make sure these are in there.

**edit** beaten

---

### Post by MnInShdw on 2007-03-31
Thanks for your help. I'm off to see if it works for me....

---

