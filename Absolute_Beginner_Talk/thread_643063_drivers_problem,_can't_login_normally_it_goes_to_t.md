---
title: "drivers problem, can't login normally it goes to text console..."
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Isfrid on 2007-12-17
Hey..

I have a huge problem. I changed something with my drivers to a VGA insted since the resulution was crap,
and so when I rebooted it kind of crashed into text console insted of graphical.
Since I'm a noob I have no idea how to fix it... 
So I was wondering if someone gets what I'm asking and can help me... 

Please and Thank you... =]

---

### Post by overdrank on 2007-12-17
> **Isfrid said:**
> Hey..

I have a huge problem. I changed something with my drivers to a VGA insted since the resulution was crap,
and so when I rebooted it kind of crashed into text console insted of graphical.
Since I'm a noob I have no idea how to fix it... 
So I was wondering if someone gets what I'm asking and can help me... 

Please and Thank you... =]

HI and you can try and boot into recovery mode this will be a command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and command ```
startx
``` or to reboot ```
 reboot
``` Hope this helps and good luck!

---

### Post by Isfrid on 2007-12-17
Thank I'll probably need it Big time... xD

---

### Post by lvleph on 2007-12-17
I will probably need this later tonight, when I install my ATI drivers. Thanks in advanced. lol

---

