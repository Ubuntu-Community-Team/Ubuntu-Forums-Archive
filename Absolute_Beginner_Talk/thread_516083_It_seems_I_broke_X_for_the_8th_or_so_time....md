---
title: "It seems I broke X for the 8th or so time..."
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by nzk on 2007-08-02
I had a problem with my xorg.conf and rather than get to the bottom of it, I did dpkg-reconfigure xorg-xserver...


Anyway, my display is now 1024x768, whereas my native resolution is 1920x1200. This is quite a problem. When I try to up my resolution to anything past 1024x768, there are so many graphical artifacts and glitches that it is completely unusable. To get an idea, imagine a baby playing with a screenshot of my desktop in Photoshop and that's close to what it looks like.

I had to go into single user mode and install xfce and kde, and I'm in KDE right now. However all the desktop environments have the same problem with going above 1024x768. Is there anything I can do besides reinstalling to get back my 1920x1200 resolution?

---

### Post by tseliot on 2007-08-02
type:
```
sudo dpkg-configure xserver-xorg
```

select the resolution you need and press ENTER whenever you don't know the answer to a question.

Then restart the Xserver

---

### Post by nzk on 2007-08-02
> **tseliot said:**
> type:
```
sudo dpkg-configure xserver-xorg
```

select the resolution you need and press ENTER whenever you don't know the answer to a question.

Then restart the Xserver

...that's the line that keeps breaking my system.

Perhaps you meant "**re**configure"? My system says 'configure' isn't found.

---

