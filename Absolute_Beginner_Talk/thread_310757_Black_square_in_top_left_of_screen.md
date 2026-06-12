---
title: "Black square in top left of screen"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by GJS on 2006-12-01
I have just upgraded to 6.10 and now I have a black square appear in the top left corner of the desktop after logging on.  The machine is a stock Dell 400SC and the monitor is a NEC multisync LCD 2070NX running at 1600 X 1200 60Hz.

The really strange thing is that if I log on as root the black square disappears, if I log on as the "normal" user, it comes back.

Any ideas?  This never happened in the previous Ubuntu version.

Thanks in advance for any help.

PS The monitor is connected via a Rextron MyHopper KVM switch

---

### Post by sakogti on 2007-02-11
I am also experiencing the same problem. I am running a IBM X Server Pentium 3, with a Samsung 19" monitor, and ATI Rage 2x AGP. Anyone know of a fix for this problem??

---

### Post by Bulltitan on 2007-04-27
Same deal here, after upgrading from 6.10 to 7.04 everything was ok but then i had the idea to
change the resolution from default to 1024X768 which is the default since i have a lcd display.
Now sometimes it goes away after a few minutes or it stays for longer, know that reconfiguring
x will fix it but why if it is the default that square shows up.

Specs: 
Laptop Compaq Presario 1700
PIII 600, 192Mb, 40Gb hdd, Ati Rage Mobility M1 (A.K.A Mach64), DVDr toshiba

---

### Post by freebird54 on 2007-04-27
Speculation here- use contents at own risk.  When I boot I get a top left corner square - but mine tells me that my gnome-settings and xserver settings are not the same.  Could it be that your 'message' is just not displaying correctly?  Does click in appropriate places near the bottom corners (say 1/4 in in) make it go away?

I repeat - *I* would try that - but you do it own risk!  :)

---

### Post by fufutos610 on 2007-04-27
My guess is that the mode-switching code is not handling the Xcursor correctly.

Try:
- not changing resolution from within the desktop, use the desired resolution at X server startup
- using the core cursor (export XCURSOR_CORE=1 or something)

---

### Post by Sleevo on 2007-05-13
Well...It might just go away by just pressing ESC or ENTER few times..but of course, you'll have to do this every time the system boot up.

---

### Post by dtgolder on 2007-12-16
Ok, I have a workaround that "fixes" this for mine (and glad other folks are having the same issue).

For me, if I open a terminal window and type any text in, the black "UPC Code" box goes away.

See if it works for you folks...obviously a problem with this system (thought I was the only one and going crazy).

---

### Post by dtgolder on 2007-12-16
Hmmm...the KVM switch might be an issue...I'm building a new box, and have it hooked to a Belden KVM...wonder if I remove that and connect directly if that'll solve the issue...are other folks using KVM?

---

