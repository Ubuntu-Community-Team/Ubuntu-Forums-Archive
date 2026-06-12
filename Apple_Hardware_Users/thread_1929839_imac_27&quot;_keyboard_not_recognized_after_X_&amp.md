---
title: "imac 27&quot; keyboard not recognized after X &amp; Kernel-update"
date: 2012-02-22
forum: Apple Hardware Users
---

### Post by opoq on 2012-02-22
Hi,

I'm having trouble since the last update (which included a Kernel, an X and an ATI fglrx update) on my 27" imac's Lucid (Kubuntu) install:

the (original wireless) keyboard is no longer working. I guess it's just not connected. This worked out-of-the-box since the original install some time two years ago.

So, to describe a little further:
- it works in EFI
- it works in Grub
- it doesn't work at the kdm-logon-screen

- it will however work when booted in safe mode using the reduced graphical interface.

I there switched to automatic login. For some reason, it'll then "normal"-boot into Gnome environment (not into KDE) - but the keyboard again isn't working.

When hitting keys on the keyboard, there will be a popup that a BT device wants to connect. I can then grant permission (using checkbox "keep permisson" or similar), but nothing changes. The popup will appear again when hitting keys.

In the bluetooth setup window, the Apple keyboard only appears shortly arbitrarily, then disappears.

I've had a look in /var/lib/Bluetooth - and the keyboard is recognized there.

What to do to make it work like it did before, ie w/o trouble? Anyone had something similar?

Thanks!

---

