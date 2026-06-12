---
title: "Macbook Pro 7.1 minor problems"
date: 2010-11-25
forum: Apple Hardware Users
---

### Post by CIement on 2010-11-25
Hi, I finally got Ubuntu working on my Macbook Pro, and almost everything seems to be working wonderfully at the moment.

I followed this guide: [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)

The keyboard lighting does work when I press the keys, but I can seemingly never lower it completely to actually turn it off. Basically if I hold it there, it will go lower, and then when it SHOULD turn off completely it goes back up to a little higher and cycles again.

Also, there's no way to right click by actually pressing the touchpad, you have to use multitouch to do it. I don't really mind this, except for whatever reason the touch to click is much much more intrusive on Ubuntu than it was on OS X. I enabled the disable tap to click while typing option but it still seems to click whenever I accidentally touch it, and the touchpad is fairly large so it's hard to avoid somewhat.

Sorry I'm really new to programming and don't really understand Ubuntu all that well, but I'm hoping I can learn a lot from the forums. Hopefully I didn't make a bad choice by being brave and jumping into the unknown world of Linux from comfortably simple OS X. Thanks for the help!

---

### Post by michal.tv on 2010-11-26
Hi Clement,

Well done for being brave and pushing yourself to learn! That's always a good thing! I'm currently also playing / learning with Ubuntu on the Macbook Pro 7.1 13" and still tweaking some bits and pieces.

There is a way of switching on the right click. Simply go to System > Preferences > Mouse > Touchpad. Then tick: [X] Enable mouse clicks with touchpad. You may also enable two finger scrolling. Works nice! You may also enable the horizontal scrolling, as by default ubuntu scrolls only vertically with this option disabled.

Then you can tap once for normal click, tap two fingers for right click, and tap three fingers for the 'third' click (same as clicking the mouse wheel).

Unfortunately I don't know the fix for the keyboard!

Best,
Michal

---

### Post by wiznillyp on 2010-11-27
If you look in your pommed configuration file  (sudo gedit /etc/pommed.conf) under #** Keyboard backlight control** what is the setting for **auto**?

If it is enabled, try disabling it and re-booting.

---

### Post by CIement on 2010-11-28
michal.tv: Well I already knew how to right click that way, but I was wondering if there was a way to right click by pressing down on the bottom left of the touchpad like in OS X. I'm glad to know I'm not the only one who is struggling but enjoying this process though!

wiznillyp: 
Thanks! That totally fixed the problem.

---

### Post by claudiobr on 2011-01-04
wiznillyp,

I'd like to thank you for helping us with this tip; I'm also a new MacBook Pro (7.1) user, and after 2 weeks with Mac OS, I missed Ubuntu so much that now my only OS is 10.10. This and the poor wireless performance when running on battery were my only problems with my hardware.

---

