---
title: "MBP will not wake from suspend"
date: 2008-05-10
forum: Apple Hardware Users
---

### Post by plague27 on 2008-05-10
Hi guys, I have a dual boot with leopard and 8.04 and whenever I suspend in ubuntu, the computer wakes to a white screen with a cursor and restarting X takes me back to refit. What gives?

---

### Post by cyberdork33 on 2008-05-10
sounds like compiz breaks, and that is likely do to a problem with the proprietary drivers you use for the video card... I would guess that your video driver is not making it back after suspend.

---

### Post by russo.mic on 2008-05-12
Which driver are you using?  I used the ATI Restricted driver and suspend and hibernate work out of the box on hardy, which is nice.  I still have to do a sudo killall atieventid to shutdown or log out for some reason.

Russo

---

