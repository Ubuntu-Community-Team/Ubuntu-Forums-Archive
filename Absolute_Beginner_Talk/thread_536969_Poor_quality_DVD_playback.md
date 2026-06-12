---
title: "Poor quality DVD playback"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-28
DVD's look great in Windows but terrible in Ubuntu.

The picture looks blocky as hell, as though the picture is being blown up.

Any suggestions anyway?

---

### Post by asmoore82 on 2007-08-28
do you have an ATI video card?
If not, what is your setup?

Also, what are you using to play DVDs?

---

### Post by AnotherMuggle on 2007-08-28
> **asmoore82 said:**
> do you have an ATI video card?
If not, what is your setup?

Also, what are you using to play DVDs?

ATI x800GTO2 Card.

Using Movie Player to play the DVD's

---

### Post by asmoore82 on 2007-08-28
ahh Excellent ...

ATI's fglrx driver does not enable "Xv" by default

"Xv" is an X11 extension specifically for high quality X-Video Overlay.

you need to add the bold lines to your /etc/X11/xorg.conf file ...

```
Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
[B]        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
[/B]        BusID       "PCI:1:0:0"
EndSection
```

the **aticonfig** command line tool should be able to do this for you,
open a terminal and run the command ...
```
~ $ sudo aticonfig --ovt Xv
```

and then restart your computer seems to be the easiest way to activate the change ...
you shouldn't have to restart, but ATI's driver has a few problems and likes to hose up when
you try to simply reload Xorg.

Also, if the video ouput is extremely freaky, make sure you have a proper DVD Decryption
library installed (libdvdcss2), mplayer and its offspring have been known to force playback
of an encrypted stream without it :p

---

