---
title: "Finally Installed, Stops Loading"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Phluxed on 2007-08-02
Hi there,
I've been trying to get Ubuntu installed for the last couple days. I finally got it installed today and am now trying to figure out why it won't load. It loaded up the first time, no problem. Everything was great. Now it loads up and just hangs at the loading bar at the very beginning.
I hit control+alt+f1 and it just says Now loading or whatever...

I tried diagnostic mode and it got to a usb interface. I unplugged a usb device and plugged it back in and everything updated immediately so it wasn't frozen. I was wondering if this is a common issue or if there is a simple way to fix it. Once I get it loading on a consistent basis, maybe I can try and get ndis installed so I can use the internet.

This IS a dual boot scenario where Vista and Ubuntu load with grub. No problems the first boot, now nothing. I didn't even make any changes to the ubuntu install, no updates or anything.

---

### Post by aquavitae on 2007-08-02
What usb device are you referring to? And what do you mean by a "it got to a usb interface"?  Try this:
Start up your computer.
When you reach grub, select the ubuntu option, and edit it.  
There are detailed instructions at the bottom of the screen on how to do this, but as far as I remember you have to press 'e'.  It will bring up a list of 2 or 3 commands, select the longest one.  
Press the button to edit the command (instructions still at the bottom of the screen)
Near the end of the line, is the word 'splash', or possibly '-splash', I can't remember which.  
Delete it and boot (I think you press 'b' to boot, but once again look at the instructions)

It should boot without the splash screen so you ca see exactly what its doing when it freezes.

---

### Post by Tux Aubrey on 2007-08-02
I think it is "quietsplash" that you will want to delete on the boot line.

---

