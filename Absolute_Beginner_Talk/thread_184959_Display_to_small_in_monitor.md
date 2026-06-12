---
title: "Display to small in monitor"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by fpt95 on 2006-05-30
Hi All, I just installed ubuntu last nite and everything seen to be ok accept the the ubuntu desktop only takes up the center of my monitor and it leaves about an inch and a half of blank monitor real estate. Can anyone give me some help.
Thanks, Frank

---

### Post by Perfect Storm on 2006-05-30
Try with

```
sudo dpkg-reconfigure xserver-xorg
```

and see if it solves your problem.

---

### Post by fpt95 on 2006-05-30
Thanks, but where do I insert that command?

---

### Post by Perfect Storm on 2006-05-30
press  <ctrl> + <alt> + <F1>
will take you out to non-gui.

First it ask for username and passsword

then 
```
sudo dpkg-reconfigure xserver-xorg
```

When done write **startx**

to come back.

---

### Post by confused57 on 2006-05-30
You may just need to adjust the settings on your monitor...using the buttons on the front to expand & move the desktop...you can try this if nothing else works.

---

