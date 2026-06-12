---
title: "ATI Radeon 7200"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-09-06
Is there a way to improve my frames per second rate.  Right now it averages 275.  I tried changing "ati" to "radeon" in the xorg.conf file, but my system would not reboot into the gui.  I had to manually restore my xorg.conf file and then the system rebooted fine.

I was thinking about getting a NVidia FX 5200 card. Money is tight for us retired people and I can't afford anything much newer than this.  Would this card give me any better FPS times.

---

### Post by ruppmeister on 2006-09-06
Hello,

Have you already downloaded the drivers for the card? If not try this site first [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

If that still doesnt resolve the problem and you still have fglrxinfo report you have mesa drivers try this site next.

[HOWTO: Fixing the "Mesa Issue" for ATI Cards ]("http://www.ubuntuforums.org/showthread.php?t=143283&highlight=ati+mesa+problem")

To see what driver you are using now try this in terminal.

```
fglrxinfo
```

in the end it should look like this with your card info in place of mine

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```

Hope this helps

---

### Post by alienexplorers on 2006-09-06
The Radeon 7200 is not able to use the fglrx drivers since it is too old.  If someone knows how to set up the "radeon" driver for this old PCI card that would be great.

---

### Post by alienexplorers on 2006-09-06
Got the radeon driver working, but still have very low fps (275).  Is there a tweak program for the ati radeon type cards.

---

