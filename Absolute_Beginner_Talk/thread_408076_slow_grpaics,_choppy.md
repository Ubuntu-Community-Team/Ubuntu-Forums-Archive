---
title: "slow grpaics, choppy"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by thedevilisbad on 2007-04-12
When I move a window around the graphic movements get really choppy. This also happens when I scroll down anything. It's is especially annoying with Firefox. Any and all help would be appreciated.

---

### Post by taurus on 2007-04-12
Sounds like you need to install a driver for your graphic card and what is your graphic card anyway?

---

### Post by thedevilisbad on 2007-04-12
I actually don't have a graphics card yet but I have integrated graphics on my Asus Motherboard. It worked fine when I was using the 7.04 live cd (I couldn't get that to install). But 6.10 is really choppy. 

Where can I find a driver?

---

### Post by taurus on 2007-04-12
Outputs of these two commands.

Applications -> Accessories -> Terminal
```
lspci
cat /etc/X11/xorg.conf
```

---

### Post by thedevilisbad on 2007-04-12
The integrated graphics is S3. What were those command supposed to do?

---

### Post by thedevilisbad on 2007-04-13
is this a common problem for ubuntu users using integrated graphics?

---

### Post by icechen1 on 2007-04-14
> **thedevilisbad said:**
> is this a common problem for ubuntu users using integrated graphics?

i has the same problem.Never got it fixed neither. :( i think is something wrong with ubuntu because i don't got problem on openSUSE.

---

### Post by Seisen on 2007-04-14
Here is the link to install the via chipset if thats what you have. I used it and it works perfectly. 

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

---

