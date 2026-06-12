---
title: "[SOLVED] Low Graphics Mode"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2008-03-06
Lesson learned, do not attach an external monitor to a laptop that is otherwise working OK on the display. At least this has been my experience. 

Gave up trying to make that work, but now each time I boot, it insists in being in Low Graphics mode, and when I configure, it has what it is supposed to be, and all works fine. 

Any way to get out of this useless loop. Read some posts, none seemed to have a straight-forward answer.

One said:

sudo dpkg reconfigure xserver-xorg

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Another referred to a link about learning all about xorg.conf (or something like that). I know if I do that, it probably will not boot up.

So, any "easy" way out of this Low Graphics routine each time I boot, or is it something I live with until I just start over.  

Sorry to sound negative, but a laptop should be able to handle an attached monitor, The monitor I attached was on the list to choose from in setting up a secondary monitor through the GUI, but it seemed to have no actual effect on implementing the selection.

Compaq 8430, the external monitor is an HP 1825. It is using the VESA Generic Video Card driver (also gave up trying to figure out the proprietary drivers.) The resolution is set to 1440 X 1050.

---

### Post by taurus on 2008-03-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

