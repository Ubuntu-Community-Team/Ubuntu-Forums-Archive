---
title: "[SOLVED] Bluetooth Keyboard &amp;amp; rEFIt don't seem to  work together"
date: 2008-08-03
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-08-03
Hi,
  I'm online with a fresh install of my Mac Mini. A lot has gone well: wireless worked right out of the box; sound is there; the screen resolution is on target.

And thanks to a HOWTO by Cyber, I got my apple bluetooth keyboard working. 

There is a problem with the bluetooth keyboard, however, that seems to occur when I reboot and have to visit the rEFIt page, where I choose which OS I want.

If I'm coming out of Ubuntu doing a restart, that's where the keyboard gets inactive and non-functional at the rEFIt screen. If I'm coming out of Mac OS X with a restart, however, the keyboard works okay at the rEFIt screen...sluggishly maybe, but it works. 

Is there ANY workaround for this? Also, booting into Ubuntu, the keyboard fails to work at the Login screen. Once I get into Ubuntu, though, it gets detected right away. I got around this by choosing to log in automatically.

I appreciate any help or suggestions. I don't know what's possible here.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-08-03
I found the answer: it's hopeless really. rEFIt states this fact very plainly:

[http://refit.sourceforge.net/doc/c4s2_bluetooth.html](http://refit.sourceforge.net/doc/c4s2_bluetooth.html)

---

### Post by cyberdork33 on 2008-08-03
Basically it will work in refit if it was setup correctly to work in the OS previous (as OS X can... probably some efi variable or something... IDK). You can get teh keyboard to work at the login screen, the issue is that you need the bluetooth connection stuff to occur at bootup. You probably have it set to "connect" in your user's startup preferences, which means that it doesn't connect until you login. 

All that generic stuff aside, I have had terrible luck with my bluetooth keyboard since Hardy. You used to be able to setup bluetooth with hidd as shown here:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

