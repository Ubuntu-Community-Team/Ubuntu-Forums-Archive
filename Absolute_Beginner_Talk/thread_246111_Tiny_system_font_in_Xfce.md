---
title: "Tiny system font in Xfce"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-28
I'm having problems with tiny fonts in xubuntu. When I freshly installed xubuntu, the font size was fine, but after using the OS for a couple of times, the font size has changed to probably the smallest size possible. The problem applies to the menu and the title bar of windows. I have tried in settings and defining font size but that doesn't seem to be working.

---

### Post by Toxicity999 on 2006-08-28
That's kind of odd... I have new no experience with xfce but a general troubleshoot for this, what updates or manual changes have happened lately?

---

### Post by k94382 on 2006-08-29
the only changes i have made is install openssh, amule, amsn, and vlc media player. i can't think of anything that would have caused this.

---

### Post by winvado on 2006-08-29
its abug in XFce

From [http://xubuntu.wordpress.com/](http://xubuntu.wordpress.com/)

1) Edit the file ~/.config/xfce4/Xft.xrdb:

mousepad ~/.config/xfce4/Xft.xrdb

And paste in:

Xft.dpi: 96

Save and exit.

2) Edit /etc/X11/xorg.conf:

sudo mousepad /etc/X11/xorg.conf


And paste in under Section "Files" (if it&#8217;s not there alread):

FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/100dpi"


cheers

---

### Post by clubsoda on 2006-11-24
After applying this and restarting with Ctrl-Alt-Backspace, I get the following:-
```
$ xrdb -q |grep Xft
Xft.antialias:  1
Xft.dpi:        96
Xft.hinting:    1
Xft.hintstyle:  hintfull
Xft.rgba:       none
```
So Xfce is good, but
```
$ xdpyinfo |grep resolution
  resolution:    86x85 dots per inch
```
How do I bring the X-Window dpi into line with the Xfce dpi, or shouldn't I worry about that?  My file
/etc/X11/xinit/xserverrc contains
```
exec /usr/bin/X11/X -dpi 100 -nolisten tcp
```

---

### Post by clubsoda on 2006-11-24
Ah, OK, I think I figured it out.  I was getting different sized fonts in the Firefox menus as compared to other system menus after using the instructions [here](http://www.linuxquestions.org/questions/showthread.php?t=257705) to enable the bytecode interpreter.  [Why isn't that standard in freetype2, now that the patent has expired?]

When editing xorg.conf I suggest a different formula for DisplaySize:-
pixelwidth/dpi*25.4 and
pixelheight/dpi*25.4
So for 1024*768 at 96dpi I've added the following line to the "Monitor" section.
```
    DisplaySize 270.93 203.2
```
This is giving me consistent menu font size between Firefox and other applications.
```
$ xdpyinfo |grep res
  resolution:    96x96 dots per inch
```

---

### Post by TuxCrafter on 2006-12-24
I may have more info about this problem

see the attachment

---

### Post by lmo on 2007-01-24
Thanks for the info.

All I needed to do was:
```
rm ~/.config/xfce4/Xft.xrdb
```
and everything worked perfectly again.

---

### Post by darthmob on 2008-07-20
> **TuxCrafter said:**
> I may have more info about this problem

see the attachment
thanks a lot, this solved the problem for me! :)

---

### Post by TuxCrafter on 2008-07-20
> **darthmob said:**
> thanks a lot, this solved the problem for me! :)
no problem nice to see it still helps people.

---

