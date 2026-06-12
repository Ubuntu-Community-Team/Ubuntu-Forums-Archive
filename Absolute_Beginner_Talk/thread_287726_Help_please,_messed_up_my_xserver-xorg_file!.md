---
title: "Help please, messed up my xserver-xorg file!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2006-10-29
Ok so I was doing fine then decided to mess with the xserver-xorg file, so now it wont boot in linux. My question is this, were exactly is that file located in the system? I just need to find it and put it back to the way it was :P Thanks!

---

### Post by willy1234x1 on 2006-10-29
I've found multiple places it could be in tell me which file exactly that you're looking for and what it pertains to (I.E. graphics etc.)

---

### Post by Daergeth on 2006-10-29
I changed my graphics driver from vesa to a different one

---

### Post by whizbaby on 2006-10-29
The x configuration usually takes place in 
/etc/X11/xorg.conf

If X doesn't start you still can switch to a terminal with ctrl-alt-F1 and edit the file with
sudo nano /etc/X11/xorg.conf

First take a look at the directory
ls -la /etc/X11/
to see if there's a backup of the file (xorg.conf.20061028 or xorg.conf~ or everything that starts with and is not equal to xorg.conf) because then you could simply copy it back
sudo cp /etc/X11/xorg.conf.20061028 /etc/X11/xorg.conf

---

### Post by willy1234x1 on 2006-10-29
ok I see you need to revert back or install new driver correctly what brand video card do you have ati nvidia or something else?

---

### Post by adam.tropics on 2006-10-29
If you don't feel too comfortable editing text files from a terminal start, then when X fails, and reduces you to a termninal, log in, then enter

```
sudo dpkg-reconfigure xserver-xorg
```

..and let Ubuntu do it all for you!

---

