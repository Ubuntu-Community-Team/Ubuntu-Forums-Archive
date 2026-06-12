---
title: "32 or 64 bit?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by roystonvasey on 2007-08-01
I installed ubuntu a while ago and forgot if I used the 64bit image or the 32bit image, is there a way to tell which I used? It's a 64 bit box so I'd get the 64 bit version, but I want to be sure.

thanks,
Simon

---

### Post by aysiu on 2007-08-01
In the terminal, type ```
uname -m
``` By the way, just because you have a 64-bit processor doesn't mean you necessarily want to install the 64-bit version. More details here:
[ How many people actually take advantage of their 64bit processor?](http://ubuntuforums.org/showthread.php?t=403064)

---

### Post by roystonvasey on 2007-08-01
thank you so much for the response! uname comes back with "i686." looks like what I should have seen if it were the 64bit install is "x86_64." correct? If so, is there a way to update my install to the 64bit flavor? Or should I start from scratch with a clean install?

As for whether or not I need the the 64bit flavor--that's a really good point to raise. I was thinking that I could render my animation a bit faster in maya as I heard 64bit XP gives you about a 15% speed improvement over 32 bit XP. I thought improvment that might carry over to linux. But if I don't have a 64 bit version of maya, it probably doesn't make a difference.

Anyway--kind of a tangent, but--does 32 bit ubuntu support 4 GB of ram? My mobo only supports 3GB of ram under winXP 32bit-- but under 64bit XP it will go up to 8.

thanks again.

---

### Post by scxtt on 2007-08-01
if you have >= 4GB of RAM, you have to use 64-bit to address it all - no way around it.

---

