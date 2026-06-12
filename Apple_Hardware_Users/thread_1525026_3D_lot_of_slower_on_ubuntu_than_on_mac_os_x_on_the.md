---
title: "3D lot of slower on ubuntu than on mac os x on the same laptop"
date: 2010-07-06
forum: Apple Hardware Users
---

### Post by acemtp on 2010-07-06
Hello,

I'm the CTO of Ryzom MMORPG. As you perhaps know, we released our mmorpg under freesoftware licence [http://dev.ryzom.com/news/13](http://dev.ryzom.com/news/13) .

I'm currently testing Ryzom on Linux and Mac OS X and here is my problem:

I have a MacBookPro 6,2 with Ubuntu 10.04 (Lucid Lynx).

When I run Ryzom on Mac OS X 10.6.4, I have about 50fps (fullscren 1680*1050).

On Lucid, I only have 15fps with the same config.

I did what it's written in:
[https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video%20&%20Effects%20%28Compiz%29](https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Video%20&%20Effects%20%28Compiz%29)

I wonder if the difference of fps is:
- due to Linux nvidia driver that is not already optimized for GeForce GT 330M
- due of something that I have badly configured
- normal

Thank you for your help!

---

### Post by cascade9 on 2010-07-06
Have you tried shutting down compiz before you run Ryzom? Compiz running has been known to slow down 3D games.

---

### Post by acemtp on 2010-07-06
Yes and it doesn't change the fps

---

### Post by cascade9 on 2010-07-06
Oh well, it was worth a try. 

It could be drivers...if you arent running the 195.xx nvidia drivers, try them (or the new 256.xx drivers, just out of beta now).

---

