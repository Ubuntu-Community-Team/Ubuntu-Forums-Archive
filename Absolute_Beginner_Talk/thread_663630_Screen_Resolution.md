---
title: "Screen Resolution"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by kboss715 on 2008-01-10
Well I figured out how to launch the Live CD (Safe Graphics Mode), but now I can't get the resolution to go above 800x600 (My LCD screen goes up to 1280x800). This wouldn't be a huge deal, except I tried to install the OS and can't see or scroll down to hit the next button during the install process. Therefore I assume I can't install until I change the resolution, which Ubuntu doesn't want me to do. :guitar:

---

### Post by Digger78 on 2008-01-10
Desktop or laptop?

---

### Post by kboss715 on 2008-01-10
Laptop.

---

### Post by Digger78 on 2008-01-10
Make and model?

---

### Post by OffAxis on 2008-01-10
never tried this on a live CD, but you could try xrandr.
```
sudo xrandr -s 1280x800
```

---

### Post by kboss715 on 2008-01-10
HP Pavilion. I will give that line of code a shot and report back in a little while.

---

### Post by Digger78 on 2008-01-10
why couldnt you boot the live CD in normal mode?

is it the same as [http://ubuntuforums.org/showthread.php?t=661550](http://ubuntuforums.org/showthread.php?t=661550)

---

### Post by kboss715 on 2008-01-10
I tried the code in Terminal, and it said "size not found in available modes". Should I go through System->Administration->Screens and Graphics and figure out what my monitor is? Also, I created this thread the other day explaining why I could not log into normal mode (different reason than the link you had provided): [http://ubuntuforums.org/showthread.php?t=662403](http://ubuntuforums.org/showthread.php?t=662403)

---

### Post by OffAxis on 2008-01-10
you could also try reconfiguring the xserver
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by kboss715 on 2008-01-10
I entered that line of code, and came up with a box to select an option (I selected the one that was selected by default). The reply in Terminal was:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20080110113058

I tried to go to Screen and Graphics and nothing has changed. Did I do this correctly?

---

### Post by mangurt on 2008-01-10
Wow, I am having the same problem, except I am using an ibook laptop.  I will give these a try when I get home!

---

### Post by OffAxis on 2008-01-10
> I entered that line of code, and came up with a box to select an option (I selected the one that was selected by default).
What one was selected by default? The 800x600?

with the dpkg-reconfigure tool you can select a number of different screen resolutions. The xserver by default will try to use the highest resolution, but if you only want to give it one option (the 1280x800) that's okay. Just be sure your monitor can handle it, otherwise you'll lose your screen (you can still network into it if you've enabled that).

---

### Post by Digger78 on 2008-01-10
I think the "alternate cd" is probably gonna be the best way to install

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  remember to check the box at the bottom for "alternate desktop CD"

Heres another site to have a read at [http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/](http://aldeby.wordpress.com/2007/09/11/howto-ubuntu-on-hp-dv65xx-series-laptop/)

---

