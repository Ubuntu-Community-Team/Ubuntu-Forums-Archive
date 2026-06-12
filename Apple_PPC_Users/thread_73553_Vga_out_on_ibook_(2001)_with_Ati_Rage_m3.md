---
title: "Vga out on ibook (2001) with Ati Rage m3"
date: 2005-10-09
forum: Apple PPC Users
---

### Post by marinaio on 2005-10-09
Hi all,
I've googled and parsed all the posts in the forum but I can't get the vga-out work.

In particular I've tried using m3mirror but since I don't have a patched kernel I get bad images on the external monitor.
I've also tried putting a "crt_display" "true" on xorg.conf ([http://www.x.org/X11R6.8.2/doc/ati5.html#17](http://www.x.org/X11R6.8.2/doc/ati5.html#17)) but it doesn't work...

Next week I'll have to present my master thesis and I'd really like to use my iBook with Gnome. Please help me :confused: :confused: :smile:

---

### Post by rapunzel on 2005-10-10
Have you tried the CtrcNumber Option as shown in this config?

[http://www.flamingspork.com/linux/doc/xorg.conf-albook-vgaout](http://www.flamingspork.com/linux/doc/xorg.conf-albook-vgaout)

It's for an aluminium powerbook, but works for my titanium as well ... maybe also on the ibook?

---

### Post by marinaio on 2005-10-11
[QUOTE=rapunzel]Have you tried the CtrcNumber Option as shown in this config?

[http://www.flamingspork.com/linux/doc/xorg.conf-albook-vgaout](http://www.flamingspork.com/linux/doc/xorg.conf-albook-vgaout)

It's for an aluminium powerbook, but works for my titanium as well ... maybe also on the ibook?[/QUOTE]

Tried and don't work.

I have to say that "MergedFB" option doesn't work too. I have to use "UseFBDev". Maybe that's the problem.

It realy seems I'll have to use MacOS for my presentation :(

---

