---
title: "Breezy screen ressolution"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by mcasanovas on 2005-10-20
Hei folks!

I've just installed a breezy and my screen ressolution came to 1024x768 max. With Hoary it was working at 1200x800.

There is a way to configure it back to 1200x800?

I've a laptop Acer 1660 with a Radeon Mobility 9700.

Thanks!

Marc Casanovas

---

### Post by Qrk on 2005-10-20
type

sudo dpkg-reconfigure xserver-xorg

into a terminal, and put in your information.

Or you can type

sudo gedit /etc/x11/xorg.conf

and type in your resolution (follow the format of those above) in the section near the bottom.

---

