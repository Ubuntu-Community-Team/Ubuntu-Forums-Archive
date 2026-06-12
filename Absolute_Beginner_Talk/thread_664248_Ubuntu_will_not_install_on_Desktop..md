---
title: "Ubuntu will not install on Desktop."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by nat6138 on 2008-01-11
So, I have been trying for about 2 weeks now, to put Ubuntu on my desktop. It's been hell.

All I get is a blinking light, and max hard drive activity/CD activity.

When I do it without the splash, I get it running decently, until GDM comes up, which it fails on.

Then it gets stuck on "Running Local Boot Scripts"

I have tried noacpi, and all that jazz.

Tried switching graphics cards, etc.

Please, any help?

Desktop specs:

1.3 Ghz Celeron
512 MB Ram
Some Intel Graphics Card

BTW: It did install once, but it had nothing. No Xorg or anything. And when I tried to enable it, it gave me a ton of errors.

---

### Post by buccaneere on 2008-01-11
File corruption on the install CD?

'Check disk for defects' at boot prompt?

---

### Post by nat6138 on 2008-01-11
Well, from what I could tell, the disk has worked on every other computer, and the md5sum is correct.

---

### Post by HemiGTX on 2008-01-11
are you using the Live CD or the Alternate cd??

if you're using the live cd try the alternate cd instead... the alternate will install in text mode.

---

### Post by nat6138 on 2008-01-11
I should have included that in the post, I tried the alternate CD. First time was that the kernel didn't install, second time was that certain packages couldn't be installed, and the last time it installed, with no graphical stuff.

The LiveCD does nothing.

---

### Post by HemiGTX on 2008-01-11
i would try to install the cli (command line interface) only at first and make sure that works ok
if all is good there instead of using gdm try installing wdm (wings display manager)
once wdm is installed install ubuntu-desktop from aptitude

---

### Post by nat6138 on 2008-01-11
When I was in the CLI, I installed ubuntu-desktop. It downloaded the packages, and I tried starting X and it did nothing except give me a bunch of errors.

---

### Post by HemiGTX on 2008-01-11
from the cli use:
sudo dpkg-reconfigure xserver-xorg
play about with the settings .. maybe a problem with X identifying your hardware??

---

### Post by nat6138 on 2008-01-11
I figured since there was no graphics. lol

Eh, I just don't get why XP goes on so well, but ubuntu won't do a thing.

---

### Post by HemiGTX on 2008-01-11
well try PCLinuxOS  its alot like XP in many ways in its layout etc... 

XP goes on so well cuz the chips were manufactcured for m$ primarily

---

### Post by nat6138 on 2008-01-11
Will try, doubt it will do much though. :)

---

### Post by HemiGTX on 2008-01-11
sorry i couldnt have been much more help to ya.. wish ya all the best in gettin that rig linux :)

---

