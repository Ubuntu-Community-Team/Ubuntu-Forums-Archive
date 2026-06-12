---
title: "need some help with new video card"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by diamantis13 on 2007-03-30
I am new in Ubuntu and Linux. My video card was recently  burnt :( ,so  I bought a new one, but I do not know how to configure it. When I boot I get a message saying that something is wrong with my X server. How can I boot in command line and what could I do next?
Thank you!

---

### Post by taurus on 2007-03-30
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
You can reboot your machine with

```
shutdown -r now
```

---

### Post by diamantis13 on 2007-03-30
Thank you :) . I Followed your instructions and I'm back to ubuntu-learning.

---

