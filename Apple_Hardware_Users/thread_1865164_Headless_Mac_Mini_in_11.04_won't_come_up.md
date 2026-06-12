---
title: "Headless Mac Mini in 11.04 won't come up"
date: 2011-10-19
forum: Apple Hardware Users
---

### Post by deja on 2011-10-19
In the past week I spent a ton of time setting up a new Ubuntu build as an AV server (and a box that I could offload 24x7 video conversion tasks to). Finally got everything set up to find that when I plugged it in where I wanted it and got it set up, X wouldn't start if a monitor wasn't plugged in. I've tried solutions presented in here to no success. X never came up or picked up an IP without a monitor plugged in, and in a few instances, X wouldn't even start when I did plug in the monitor. It's set to auto-login to Gnome in Ubuntu Classic, and the keychain has no password set.

I considered rolling back to 10.04 and trying there, since those responses all dealt with the older version, but I compiled my own versions of a few software packages and the idea of going back and doing it all over again stresses me out. Anyone know what it takes to make this work?

This will be set up by my TV without a monitor or keyboard/mouse plugged in, just a hard drive, with the occasional VNC access needed.

Thanks
-d

---

### Post by deja on 2011-10-24
Any help?

---

### Post by deja on 2011-10-29
Bumpity

---

### Post by rcmn on 2012-05-26
[http://blog.nickoneill.name/headless-mac-mini-with-ubuntu.html](http://blog.nickoneill.name/headless-mac-mini-with-ubuntu.html)

"...The solution is stupidly simple. VGA connections can “simulate” a monitor by having resistance across 3 sets of pins. This can be done by literally inserting resistors into a VGA connector, as shown below. It’s the DVI-to-VGA connector that shipped with the mini.

DVI to VGA adapter with resistors

I searched around for exact specifications and most people say 75 or 68ohm resistors (purple-green-black or blue-gray-black). I only had a few 68ohm resistors on hand so I used those. Apparently anything from 50-150ohm will work (not tested, explosions lol!)..."

I did test it because that is my setup. 3$ at the nearest shop.

---

