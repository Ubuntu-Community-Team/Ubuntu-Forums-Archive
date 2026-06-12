---
title: "Can't change refresh rate?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by LingLing1337 on 2007-08-24
Okay, the current refresh rate is 85 hz, and my monitor only handles 60hz, and it's bugging the hell out of me to switch it. Newbiew question, I know, but using the dpkg-reconfigure xserver-xorg command, is there a  way to enable other refresh rates? I don't even know how to check a box when it asks which resolutions to use. I assumed enter, but I was wrong. I cant directly edit xorg.conf since it says I'm not the owner (this is the account I setup on install). Any help?

---

### Post by crjackson on 2007-08-24
Open up a terminal session and paste this line of code into it.  Then hit enter.

```
sudo nano /etc/X11/xorg.conf
```

Enter in your password and hit enter.

This will allow you to edit the xorg.conf file.

---

