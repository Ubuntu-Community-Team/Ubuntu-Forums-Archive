---
title: "Radeon mobility m11/9700 works almost default on Clevo d470k/Sager 4750/Python d470k"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by rune_kg on 2006-06-12
Hi guys

Just installed dapper and was dismayed that only 1024x768 screen resolution worked. So I tried changing the 'driver' setting in /etc/X11/xorg.conf to vesa, but that did no good either. What did the trick was simple running:

sudo dpkg-reconfigure -phigh xserver-xorg

as implied in xorg.conf.

Now it is smiling away with its maximum resolution of 1440x900.

Lets hope dapper stays as happy in the future for me.

Rune Kaagaard
Copenhagen

---

