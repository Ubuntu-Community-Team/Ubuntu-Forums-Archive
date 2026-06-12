---
title: "[SOLVED] 3-button mouse"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-11-19
I just got a generic 3-button mouse installed on Badger. The middle button doesn't work. I read about xorg.conf, but can't figure out how I should change it. Or even if that is what I should do.

Suggestions

Gary

---

### Post by Ecthelion on 2006-11-20
First of all backup your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```

If you have troubles after reconfiguring your xserver you can always go back using
```
sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf
```

After backing up your xorg.conf file, reconfigure your xserver
```
sudo dpkg-reconfigure xserver-xorg
```
While reconfiguring you will be asked if you want to emulate a 3-button mouse, say yes.
For all th other questions, you better leave the option that it choosed for you.

---

### Post by Gary Nored on 2006-11-20
Thanks for the suggestion. I did it, and the middle button is now responding ... sorta. The only thing I've found that it does is close a tab in Firefox. 

I thought that cut and paste operations were mapped to the middle button. Or am I just daydreaming? 

BTW -- I checked xorg.conf and it's correct. 

Gary

---

### Post by melancholeric on 2006-11-20
Select with mouse = copy
Middle click = paste

I think firefox opens links in new tabs with the middle button too.

Opera can scroll with it, close tabs, open links in new tabs ... and paste. Scrolling is one of the main reasons I prefer Opera.

---

