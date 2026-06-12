---
title: "Can't change resolution - stuck at 640x480"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-26
I rebooted my computer, and then it just started in 640x480, and it was the only one listed under  where you change the resolution. Any ideas?

Thanks

---

### Post by taurus on 2007-01-26
Have you installed a driver for your graphic card and what is it anyway?

---

### Post by Skyler0 on 2007-01-26
Yeah, I have the fglrx drivers installed afaik.

---

### Post by taurus on 2007-01-26
Which ATI card is it?

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Skyler0 on 2007-01-26
I tried that repo and it did update the driver, but the resolution is still stuck.

and I have a Radeon 9550GE, but I've never had a problem before with the drivers (had beryl installed before format aswell, and it was working fine.

---

### Post by geezerone on 2007-01-26
Try **"[COLOR="RoyalBlue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]"** to add resolutions. Check which resolutions exist in your "xorg.conf" file.

---

### Post by Skyler0 on 2007-01-26
that worked. Thanks :)

---

