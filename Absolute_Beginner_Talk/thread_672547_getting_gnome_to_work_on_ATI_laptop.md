---
title: "getting gnome to work on ATI laptop"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2008-01-19
I just installed Ubuntu 7.10 on a Toshiba laptop. The live CD worked fine, but when I installed it onto the hard drive, it won't show any graphics, only terminal. When try "sudo startx" it tells me it sees no screens. Please help!

---

### Post by billgoldberg on 2008-01-19
Reinstall it, it will most likely fix the problem and as you know will only take 15 min.

---

### Post by nbv4 on 2008-01-19
how would that change anything? if it wouldn't work the first time, why would reinstalling it do anything?

---

### Post by sloggerkhan on 2008-01-19
It does seem really odd that the live CD would work and then you have no graphics. My first thought would be that the install had an error somewhere.

If it's the same on the 2nd install, what is the graphic card/chipset?
May be a missconfigured X or something.

---

### Post by nbv4 on 2008-01-19
I just fixed the problem. I followed the instructions found here: [http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

and instead of selecting "vesa", I selected "ati" from the driver list. Now I get graphics!

---

### Post by sloggerkhan on 2008-01-19
Just a misconfigured x server, then.

---

