---
title: "screen resolution problems"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by pete_zahuat on 2008-03-14
I was trying to figure out how to get my s video working in ubuntu.  I was reading on a forum (don't remember which one) and it suggested to change the screen resolution to 800x600.  I changed it and rebooted like it said and now when the login screen is supposed to be up, it is nothing but a few symbols scattered on my screen.  Is there an easy way to change it back to the default setting or am I really screwed here?

---

### Post by SOULRiDER on 2008-03-14
Try and reconfigure Xorg.
First go to a tty console by pressing ```
ctl + alt + f1
```
log in and use this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Finally, press ```
alt + f7
``` to go back to GDM and press
```
ctrl + alt + backspace
```

---

### Post by pete_zahuat on 2008-03-14
no luck with that... should I just do a fresh install?

---

