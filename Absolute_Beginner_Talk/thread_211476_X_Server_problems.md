---
title: "X Server problems"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-07-08
every now and then when i turn on my computer...i get a error saying "Failed to start X Server..." and i can log in but its like all like the terminal

---

### Post by PingunZ on 2006-07-08
type sudo nano /etc/X11/xorg.conf

then post it here of try to fix it ..
Have you followed a howto about xgl, mouse configuration, ... ?

Grtz PingunZ

---

### Post by Sonofmoog on 2006-07-08
I get a similar error where Ubuntu boots and the resolution is all wrong.  It's intermittent and a reboot fixes it, so I don't worry about it.  If you wish to check further, you might run

```
dpkg-reconfigure xserver.xorg
```

This will open an interactive configuration tool where you can adjust your xserver settings.  You should have hard copy manuals of both your monitor and graphics card handy.  You may need the information in them.  But, I'll say again, if your problem is intermittent, it's probably not worth the risk running this ..

---

### Post by notjohn101 on 2006-07-08
its blank

---

### Post by DSn0wMan on 2006-07-08
Be sure to use a capital "X" in the "X11" part of the path "/etc/X11/xorg.conf".

---

### Post by notjohn101 on 2006-07-08
i did put a capital X...its still blank

---

### Post by DSn0wMan on 2006-07-08
then you need to run ```
sudo dpkg-reconfigure xserver-xorg
```

This will let you set all your options, and it wrights to /etc/X11/xorg.conf

---

### Post by notjohn101 on 2006-07-08
wait...

sudo dpkg-reconfigure xserver-xorg

or

dpkg-reconfigure xserver.xorg


because both have been mentioned

---

### Post by confused57 on 2006-07-08
> **DSn0wMan said:**
> then you need to run ```
sudo dpkg-reconfigure xserver-xorg
```

This will let you set all your options, and it wrights to /etc/X11/xorg.conf

Run this one.

---

### Post by notjohn101 on 2006-07-08
ok

---

### Post by Sonofmoog on 2006-07-08
> **notjohn101 said:**
> wait...

sudo dpkg-reconfigure xserver-xorg

or

dpkg-reconfigure xserver.xorg


because both have been mentioned

Hyphen, not period.  My bad

---

