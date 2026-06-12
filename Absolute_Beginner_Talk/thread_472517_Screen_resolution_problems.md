---
title: "Screen resolution problems"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by dua on 2007-06-13
Hi all,

I realise screen resolution has been addressed at some length, but I can't find a solution to this particular problem.

The screen resolution on boot is stuck really low. We managed to get through the install procedure using Alt+F7 and having done that, stopped gdm, ran dpkg-reconfigure xserver-xorg and the resolution was fine. However, now whenever we boot, we have to go into a terminal and stop and start gdm to get back to the proper resolution.

I can't work out why it seems to be using the wrong config file on boot up but the right one when we restart gdm. I've tried renaming/moving everything from ~/.gconf/desktop/gnome/screen and that doesn't help either.

Any ideas?

Thanks!

---

### Post by blue_shift on 2007-06-13
Have you tried editing xorg.conf directly?

---

