---
title: "Screen Resolution"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by d4v1d on 2007-01-21
I have installed 6.10 on a PIII machine with an Intel 815 integrated graphics chipset. At resolutions above 1024*768 I get vertical interference lines and screen artifact. The chipset (and monitor) should support resolutions above this. What could the problem be?

ta
David

---

### Post by rai4shu2 on 2007-01-21
My guess is that your monitor isn't being detected properly. Try reading through this:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by riven0 on 2007-01-21
Most likely you need the 915resolution. So install it:

> sudo apt-get install 915resolution

Then [follow this howto]("http://ubuntuforums.org/showthread.php?t=269052") to get it setup correctly.

---

