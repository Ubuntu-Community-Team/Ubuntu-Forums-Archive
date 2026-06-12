---
title: "Run fluxbox"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2006-01-20
I am a XUBUNTU user (breezy, on P# laptop.


I tried to use fluxbox, after i installed:
```
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

```

now it tells me to type startx and fluxbox will start, but after typing startx my XFCE comes up again. 

QUESTIONS:
Where can I find good explanations about xserver.
How do i change the configurations so when i type xserver I won't go into my XFCE GUI but into fluxbox. (ANd how do i change it back to XFCE, incase I don't like it :) )

---

### Post by morphodone on 2006-01-20
does your system boot into a graphical login? like gdm or kdm?

if so you can specifiy which desktop to boot into...

if not, sudo apt-get install gdm

---

### Post by mr_ed on 2006-01-20
If you don't go the gdm route, try adding a file called .xinitrc into your home folder if there isn't one there already.
If it's empty, just add one line:
```
exec fluxbox
```

If you want to revert back to XFCE, I think you're supposed to put
```
exec startxfce4
``` but I'm not positive about that.

This is some of the documentation for fluxbox.
[http://fluxbox.sourceforge.net/docbook/en/html/](http://fluxbox.sourceforge.net/docbook/en/html/)

Oh, and you should *definitely* run the devel version if it's available.  The "stable" one hasn't been updated for several years.

---

