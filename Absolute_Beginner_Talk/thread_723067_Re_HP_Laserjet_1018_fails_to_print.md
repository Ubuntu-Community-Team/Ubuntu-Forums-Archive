---
title: "Re: HP Laserjet 1018 fails to print"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by tedrampart on 2008-03-13
I'm in the same boat.. I recently got a new computer here at work, and now I have 7.10 running on it..

the printer worked great on 6.06, but when I moved everything over to the new computer, the printer just doesn't work.  It works in windows fine, but when i try it in ubuntu, its got nothing..

I've tried the foo2zjs script (which is how I got it to work in 6.06), but its not working.. I've tried over and over, from lpd, to ipp... I'm almost considering either setting up the old computer as a print server, or flat out begging the boss for a new printer (since it works in windows I bet its not gonna happen)..

I've even tried installing it on my laptop (also 7.10) and it doesn't see it either..

lsusb shows nothing..  

everywhere I look, it says it works fine, people say they got it to work no problem.. but they don't explain how..

should it be detected by system-config-printer as soon as its loaded up?

---

### Post by Sef on 2008-03-13
Moved to its own thread.  The reference is to this [thread]("http://ubuntuforums.org/showthread.php?t=710805").

There is [required plug]("http://hplip.sourceforge.net/supported_devices/laser.html")-in that you need.  The site does not say what it is or where to get it though.

---

### Post by tedrampart on 2008-03-13
okay, I downloaded the HPlip package, and found the plugin for my printer, but I'm not sure how to go about this, since the printer isn't detected when plugged in...

---

### Post by tedrampart on 2008-03-17
okay, the HPlip plugin and setup still didn't work.  

in dapper it would detect the printer after running the driver script.. now in gutsy it just doesn't find it at all.. not through lsusb or the printer config programs..

---

