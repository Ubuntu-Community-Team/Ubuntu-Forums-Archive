---
title: "new monitor"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by kman14 on 2006-11-11
just got a new monitor.

LG 19 inch flatron L1952S.

when i check in /X11/xorg.conf (i think that's where) it tells me that i'm still using my old monitor.

is there an easy way to change this.

i assumed it would recognise the new one.

thanks.

---

### Post by bodhi.zazen on 2006-11-11
Try:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
```

---

### Post by aidanr on 2006-11-11
alright the things you'll want to change in xorg.conf:

```
Section "Monitor"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0


Section "Screen"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
```

that should do the trick, i looked up the horizontal and vertical frequencies on the lg site

edit:// or what bodhi.zazen said;)

---

### Post by kman14 on 2006-11-11
aidanr

thanks for that.

it worked a treat.

good work.

---

