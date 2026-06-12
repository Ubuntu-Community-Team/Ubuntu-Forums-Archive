---
title: "Screen resolution too small after installation"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by womblet on 2007-01-14
My screen size is too small after I installed ubuntu 6.06. I installed windows xp first, and didn't reinstall any xp drivers before installing ubuntu - I don't know if that effects the screen size or not - I would have thought it was separate but it was the same incorrect size in both.

I tried running the autodetect script from help.ubuntu but it didn't solve the problem. Would appreciate any advice - I'm new to ubuntu, have been using it for a day.
Thanks

---

### Post by bodhi.zazen on 2007-01-14
first, your windows drivers will not affect Ubuntu and visa versa :p

You can try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that fails, video card ??

Monitor ??

---

### Post by gentlemanmasher on 2007-01-14
Can you try going to System=Preferences=screen resolution

---

### Post by womblet on 2007-01-14
Thanks, I tried both but no luck, It is a flatscreen on a laptop if that makes a difference.

---

### Post by bodhi.zazen on 2007-01-14
Laptops can sometime be a pain ....

What laptop ?

The last time I fiddled with a Dell I have to update the bios and add some info to xorg.conf

You likely need to add horizontal and vertical refresh rates to xorg.conf.

See this thread:

[http://www.ubuntuforums.org/showthread.php?&t=269052](http://www.ubuntuforums.org/showthread.php?&t=269052)

---

### Post by womblet on 2007-01-14
Its a dell latitude d620, screen size 1440 x 900 - I'm working through that link you sent, The strange thing is I previously installed ubuntu and it worked fine the first time. Which I don't understand

---

