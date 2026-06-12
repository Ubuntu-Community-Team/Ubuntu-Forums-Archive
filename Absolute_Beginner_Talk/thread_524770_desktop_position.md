---
title: "desktop position"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by bakerbaz on 2007-08-13
Hii peeps,
  when I  iinitially booted-up I had a half inch gap on the left side of my monitor.
I ran the restricted device driver for my NVidia graphic card ,rebooted and now
there is a 1 inch gap on the right side.
   i presume this can be adjusted with xorg or xserver....but how?
                  please help
                      a,n.other idiot  [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)
:lolflag:

---

### Post by Hospadar on 2007-08-13
I would bet that this is just a monitor problem.  Are you using an analog (vga) monitor cable?  If you have a lcd monitor with an auto-adjust feature, try using that, or try changing the H-position on the monitor.  I know sometimes my machine has a notably different h-postion in windows or linux when using the analog connection.

If that doesn't do it, try poking around nvidia-settings in Applications->System Tools->Nvidia Settings

---

### Post by heimo on 2007-08-13
> **bakerbaz said:**
> there is a 1 inch gap on the right side.
   i presume this can be adjusted with xorg or xserver....but how?
                  

Or monitor's geometry settings. If that's not an option, xvidtune can tweak modelines, which can be put to xorg.conf

---

### Post by por100pre1 on 2007-08-13
Yes, adjust xserver-xorg:

Crtl+Alt+F1, login and then:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

```
sudo dpkg-reconfigure xserver-xorg
```

and follow instructions, finally

```
startx
```

or:

```
reboot
```

---

