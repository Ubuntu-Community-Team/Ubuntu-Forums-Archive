---
title: "Vga Driver For Ubuntu"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2007-06-09
Hi I Hvae Install Ubuntu On A Old Celron And There Are Only To Resolution I Can Get 800x600 And 640x400 How Do I Fix It. Ot Was Running Up 1024x1200 On Xp

---

### Post by BarfBag on 2007-06-09
What kind of graphics card does it have?

---

### Post by NeoLithium on 2007-06-09
Open up a terminal (Applications -> Accessories -> Terminal) and type ```
lspci
``` And copy and paste the output so we can see what driver you need :)

---

### Post by taurus on 2007-06-09
What graphic card do you have on that machine?  Perhaps you need to install a driver for it first before you can go into a higher resolution.

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by Brendan Hart on 2007-06-09
I think thats the issue with all operating systems, i got a monitor goes up to 1680 by 12xxx or something, and it wouldnt go higher then 1024x768 till i installed the drivers
thats even with windows xp

---

### Post by w4ett on 2007-06-09
Also please post your xorg.cong file from:  gedit /etc/X11/xorg.conf

---

