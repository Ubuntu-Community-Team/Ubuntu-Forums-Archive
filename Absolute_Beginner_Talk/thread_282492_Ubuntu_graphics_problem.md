---
title: "Ubuntu graphics problem"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Tanner31593 on 2006-10-22
hey,


Recently i tried to boot into ubuntu,


but it said there was an error with my graphics,
and the screen was blue with white characters on it,

i dont remember what the exact error said,

but it wouldnt let me boot into ubuntu,

this has happened 2 times in the last 2 weeks,
and both times ive reinstalled ubuntu,

but can it have something to do with my screen resolution????

Ive noticed that the text and such in ubuntu is awfuly small,


idk,

can any1 think of an explanation with so little details???


Tanner.

---

### Post by BitTorrentBuddha on 2006-10-22
The blue screen is a result of an error found in your xorg.conf file, after the message, if you select OK (using the arrow keys and enter,) you should find yourself at a terminal, or press control + alt + F1. At this terminal you can restore your old xorg.conf (assuming you made a backup before doing whatever it is you did to it) by running:```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
*replace /etc/X11/xorg.conf.bak with whatever you named the backed up file.*

---

### Post by Tanner31593 on 2006-10-24
ok,

Well i havent done anything to it to make it do that (that i know of) i havent really done anything on ubuntu except TRY to install wine ((error: dependency not satisfiable)) any anyway,

how do i make a backup??

---

