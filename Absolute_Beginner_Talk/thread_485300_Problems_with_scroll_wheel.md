---
title: "Problems with scroll wheel"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by FritzBrown on 2007-06-26
I just bought a Logitech Trackman Wheel (I have a couple of others on other computers and love them) to use with my Sony laptop, running Xubuntu (Dapper).  It is plugged in using the PS2 adapter.

It works fine, except the scroll wheel doesn't scroll.  The touchpad still works, and it scrolls (toward one side, it acts as a scroll wheel) just fine.  The scroll wheel *does* work when plugged into my WinXP box.

I don't find anything to help in *Mouse Setting*, and xev gives me a box to (I presume) test what happens when I click, etc.  Absolutely nothing happens when I scroll the mouse.  (Nothing appears to happen when I do the scroll thing with the touchpad, either.)  Clicking the scroll wheel does work as a middle button.

Help! :cry:

(Oh, and I didn't find this issue in another thread.)

---

### Post by w4ett on 2007-06-26
Sounds like you installed without you mouse connected maybe?  If so:

sudo dpkg-reconfigure xserver-xorg

will allow you to set your mouse settings

---

### Post by FritzBrown on 2007-06-29
Right, I loaded xubuntu with no external mouse.  I will try the *reconfigure*.

---

