---
title: "Massive Gutsy Wireless Bug..."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2007-10-19
On some wireless bcm43 cards, the wireless connectivity works great after installing the restricted drivers, until you restart, where it is impossible to join a network, or nm-applet cannot find any networks at all, even though the wireless light is on. Anyone else getting this? :(

---

### Post by Mazza558 on 2007-10-19
Well, this is just gettng wierder and wierder. I completely removed "bcm43-fwcutter", restarted and it connected to my network. I'm getting about 50b/s (yes, bytes) download speed, and google takes roughly 20 seconds to load. What's up?

---

### Post by Joakim Stokland on 2007-10-19
I don't know, but doesn't Linux try to make any hardware work? Just wild thoughts, but I know that Linux is able to make very much hardware work, so maybe it actually gets the card running. -Poorly though. And maybe the restricted driver is defective somehow, but still "preferred"?

---

### Post by Joakim Stokland on 2007-11-22
Hi again! I just came over this thread again, after trying to make my girlfriend's computer work. She does too have that very same Broadcom wireless card ( BCM4318 ). She did experience the same problems as you. The problem is that this Broadcom device is not fully supported under Linux, and is therefore unstable.
Since I visit my girlfriend only every third week or once a month, I've got too little time trying to make it work, but during my fight, I've found some links that may help you - they have helped others. Hope you can make it work!

These threads regard your card and may be helpful:
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Here's a guide to general wireless-troubleshooting:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I suggest the first thing you do is have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
If you are lucky enough to make that application work, it will save you a LOT of work!

Good luck! And let me know if you make it work :)
Joakim

---

