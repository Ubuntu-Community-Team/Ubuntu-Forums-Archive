---
title: "Old mouse plug and Ubuntu."
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by daush on 2005-05-31
Hi hi. i like ubuntu, so i pass they to my girlfrined use in tje oldpc that she has.
firist bco'z to me and she is to dificult install the modem adsl (300kbps) USB in windows 98... so we try ubuntu to reconize the modem usb (they do fine with the mine)
.
but.. the mouse is tottaly freeze!!! don't move... and don't.
the mouse is old too. the connection it's oldest then ps2.. if i buy a conector to put my mouse ps2 in his oldest jack? like a tranformer. O.o
work?

---

### Post by thrift on 2005-05-31
Are you using a serial connector for the mouse?  please try to speak more clearly it's hard to understand what you are saying.

Ubuntu should would work properly with a serial mouse, though I've never tried it, but you probably just need to edit /etc/X11/xorg.conf and specify the ttyS0 device.  

If you do want to just get a Serial to PS2 converter they do make those, so that works as well.

---

### Post by daush on 2005-05-31
thanx. i will try the conversor.. if not i buy a USB mouse

sorry for speek so confuse.
i from chile and my english its tooo bad

---

### Post by thrift on 2005-05-31
No problem, it's just the ... and stuff didn't help with the poor english.  It's ok though :).  A converter will work, but if your comfortable editing /etc/X11/xorg.conf, you can probably make it work for free.

Your choice.

Good Luck.

---

