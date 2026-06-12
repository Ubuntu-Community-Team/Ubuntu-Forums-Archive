---
title: "X server fatal error"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by sanvig on 2006-12-26
So, got things running - [Re: This thread]("http://ubuntuforums.org/showthread.php?t=324182").

Now I'm stuck with the X problem.

It stops and reports an error
[INDENT]
Fatal server error: No screens found[/INDENT]

Before that it detects the GFX as a ATI R430 (X800-XL) as it should, and then these two lines:

[INDENT](WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 1:0:1 could not be detected![/INDENT]

Is this a driver problem, or something completely different?

(If something needs to be manually edited somewhere in a conf-file, please specify what editor - Gedit won't start)

---

### Post by taurus on 2006-12-26
If you need to edit something from a console/terminal, then use nano...  Otherwise, boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by sanvig on 2006-12-26
> **taurus said:**
> If you need to edit something from a console/terminal, then use nano...  Otherwise, boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

Thx but didn't help. Still:

[INDENT](EE) No devices detected

Fatal server error:
No screens found[/INDENT]

---

### Post by taurus on 2006-12-26
Then do the old fashion way (from recovery mode).

```
dpkg-reconfigure xserver-xorg
```
(Pick "vesa" as the driver for your graphic card and once you have X running again, then install the right driver for it.  And if you are not sure about an answer, just take the default...)

---

### Post by sanvig on 2006-12-26
Heck. I chose VESA, defaulted all along and went for an absolutely WillWork 800*600 60Hz with 16 bit color depth.

Now something happens and the monitor switches off ... :-(

(Monitor's fine, it just ends up in some unsupported mode I guess)

---

### Post by mrv on 2007-01-12
You should do sudo gedit /etc/X11/xorg.conf, find a line 'Driver "ati"' and change it to 'Driver "radeon"'. There's a problem with autodetecting some of the newer ATI Radeon cards... which will hopefully be fixed finally in the next Ubuntu (and other distributions).

---

### Post by mrv on 2007-01-15
Should be apparently fixed just now, in the newest [daily images](http://cdimage.ubuntu.com/daily-live/). But not in Herd 2, since the fix went in just after it.

---

