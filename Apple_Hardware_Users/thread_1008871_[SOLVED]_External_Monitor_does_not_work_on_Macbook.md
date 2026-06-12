---
title: "[SOLVED] External Monitor does not work on Macbook Pro 4,1"
date: 2008-12-12
forum: Apple Hardware Users
---

### Post by _alex_ on 2008-12-12
Hey Guys,

Did anyone have any luck getting an external monitor to work with Macbook Pro 4,1?

I've ran "sudo dpkg-reconfigure -phigh xserver-xorg" with the external monitor plugged in to the DVI port (following instructions at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) ).
My xorg.conf looks as follows:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

The external monitor doesn't seem to be detected. Only my main screen appears in gnome-display-properties. Here's the output of "xrandr -q":
```

Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   ... more resolution lines cut out ...

```

Any suggestions on how to fix this? Note that this is also missing from the wiki pages. I'd be more than happy to add it, once I get it to work myself.

Alex

---

### Post by pennstatebadboy on 2008-12-12
I have a slightly different problem. My system recognizes the external monitor (connected via DVI), but won't display anything on the external monitor's screen.

Some people have found that DVI out works when they boot from the Live CD. No idea why, but you could try.

---

### Post by cyberdork33 on 2008-12-12
You might need to boot with the display connected to get it detected.

---

### Post by _alex_ on 2008-12-12
Got it to work. Turns out one has to use nvidia-settings instead of the gnome-display-properties. Works like a charm. Plug in external monitor, click "Detect Displays", configure setup (clone or dual), hit apply, done.

Edit: I added instructions to the wiki: [https://help.ubuntu.com/community/MacBookPro_Penryn#External%20Monitor](https://help.ubuntu.com/community/MacBookPro_Penryn#External%20Monitor)

---

