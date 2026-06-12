---
title: "resolution problem"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by brywayripp on 2007-06-04
I can not get the resolution to change on my computer it is stuck on 640 x 480. it use to show three i could choose from but now I have only 1

---

### Post by taurus on 2007-06-04
You can edit /etc/X11/xorg.conf add other resolutions in there if you wish, toward the end of the file.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```
And don't forget to install a driver for your graphic card if you plan to go to a higher resolutions.

---

### Post by brywayripp on 2007-06-04
When I first intalled I had all three resolution choices but I only have one choice now. Every now and then I can get it to change but not very often.

---

