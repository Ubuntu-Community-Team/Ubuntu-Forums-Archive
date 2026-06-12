---
title: "Big trouble"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by dudeness3 on 2007-02-16
Last night I installed 6.10 Edgy, I was in love, then, I was messing around with Beryl and other things like kiaba dock or whatever it's called, well, as I knew, it crashed, and this morning, my mom and sister missplaced the CD I had written the .iso onto, I still cannot find it, lol.
Well I downloaded it again, wrote another CD, 3 in fact, and all have Buffer errors when starting, what does this mean? I can't even start the live CD, I hope someone can tell me what to do.
And I'm out of CDs lol

---

### Post by taurus on 2007-02-16
Why don't you try to fix X instead of trying to reinstall it.  Boot into recovery mode from GRUB menu and at the prompt, do

[code[dpkg-reconfigure xserver-xorg
(And if you don't know the answer to a question, just take the default value and use vesa as a driver for your graphic card.)
shutdown -r now[/code]

---

### Post by dudeness3 on 2007-02-16
Thats the thing, I reinstalled 6.06 Dapper after they all failed, I know it was a stupid thing to do, but I didn't know what else to do.

---

