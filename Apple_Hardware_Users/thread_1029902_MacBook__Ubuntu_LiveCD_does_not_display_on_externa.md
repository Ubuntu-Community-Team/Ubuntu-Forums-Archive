---
title: "MacBook:  Ubuntu LiveCD does not display on external monitor"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by jrrivera on 2009-01-03
I have two MacBooks:
[INDENT]MacBook2,1[/INDENT]
[INDENT]MacBook4,1[/INDENT]

Neither of these have a working LCD, so I attached an external monitor (Apple 20" Cinema).  I figured I'd install Ubuntu (Desktop) on both and treat these as headless servers, perhaps make a tiny cluster from the two.

Unfortunately, when booting from the Ubuntu LiveCD, the OS doesn't send the display data to the external monitor.

The LiveCD boots (I have successfully installed it on one of the systems using sheer guess work and defaults - no video still, though), but it would be of considerably more consequence to know what I'm doing.

Any ideas on how I might get this to work?

Initially I thought (and it may be the case) that the solution involve changes to the EFI settings, but two days of searching have yielded nothing of consequence.

Further, it seems to be the LiveCD as I can boot other OS from CD with no problem (Leopard installer, e.g.).

Any ideas?

Many thanks!

-José

---

### Post by cyberdork33 on 2009-01-05
believe that the output is controlled via software, and the default is of course to display on the internal screen.

If you are wanting a headless server, you might be able to get a ssh server going on the machine, then ssh in to do the installation.

---

