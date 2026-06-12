---
title: "right-click functionality - macbook + gutsy tribe 5"
date: 2007-09-22
forum: Apple Intel Users
---

### Post by Zelut on 2007-09-22
I've been running ubuntu on my macbook (second gen, C2D) since the beginning of the year.  Everything works great however recently with one of the 7.10 updates I have lost my right-click functionality.

Can anyone share their xorg or steps to get synaptics touchpad right-click functionality?  I would appreciate it.  The old xorg.conf that I was using (previous to gutsy) kills all synaptics functionality so a revert doesn't work.

---

### Post by alephsmith on 2007-09-22
I believe the option is:

```
Option "TapButton2" "3"
```

However it didn't work that well for me, I am going to do a fresh install of Gutsy so I'll try to report back then.

---

### Post by alvinwu on 2007-09-22
Hi, click into the ->Preferences ->Mouse,

then choose "Touchpad"
then "Tap to Click"

Then the click and right-click function should be back to normal.

---

### Post by Zelut on 2007-09-24
it looks like that might have done it, although my sensitivity still is pretty bad.  If anyone has a good working config that they can share I'm sure a lot of people would appreciate it.

---

### Post by cyberdork33 on 2007-09-24
In the faq:
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

---

