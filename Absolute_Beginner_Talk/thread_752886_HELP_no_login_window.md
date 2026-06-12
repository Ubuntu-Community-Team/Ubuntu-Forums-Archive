---
title: "HELP no login window"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by laffinet on 2008-04-12
I somehow messed up my system.

My laptop boots up normally but when it should load the login window all I get is a black screen and the mouse cursor runnign on the little rotating bit forever.

I suspect I  may have messed things up when changing the login window but I'm not sure.

Thanks for any help.

---

### Post by Crafty Kisses on 2008-04-12
At the black screen, try doing the following:
```
startx
```
If that doesn't work, it sounds like you messed up your X, which you can reconfigure by doing the following:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions as best as you can, then reboot, and you should be good.

---

