---
title: "log in screen stuck"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by DavidOhio on 2007-01-13
I tried to install the drivers for my GeFroce 6600 AGP 256mb card. I thought it was going well for my first try. Guess not. I missed #7 on the guide. Now 6.10 stops at the log in screen. I can move the mouse but I can't type in the box and I have to hit the reset button get out of it. I put 6.10 on it's own hard drive so I have no way to acess it form winxp. How can I get around the log in page? Or can I?

---

### Post by taurus on 2007-01-13
Boot into recovery mode from GRUB menu and reconfigure X again.  Try to use vesa driver for your graphic card for now and reinstall nVidia again by using this guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

```
dpkg-reconfigure xserver-xorg
```

---

### Post by DavidOhio on 2007-01-13
I'll give that a try. Thanks

---

### Post by DavidOhio on 2007-01-13
That worked!  Thanks.  Now to try again to get the drivers in.

---

