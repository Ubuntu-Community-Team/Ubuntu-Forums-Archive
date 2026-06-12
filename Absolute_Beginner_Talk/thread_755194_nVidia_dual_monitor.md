---
title: "nVidia dual monitor"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by csantama on 2008-04-14
I'm using nvidia geforce graphic card with two monitors. When I enable it on restricted devices, then the resolution in both monitors is at 800x600 and there's no possibility to change the screen resolution. On the other hand, if I enable "TwinView" in xorg.conf "Layout", to get the two monitors working, I get two clone screens with the resolution at 800x600 in both of them.

Does anybody know how to set both monitors at 1280x1024@75 as a spanned screen, where windows can be dragged from one to the other?
I hope someone could find an interesting and effective answer.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by stchman on 2008-04-14
> **csantama said:**
> I'm using nvidia geforce graphic card with two monitors. When I enable it on restricted devices, then the resolution in both monitors is at 800x600 and there's no possibility to change the screen resolution. On the other hand, if I enable "TwinView" in xorg.conf "Layout", to get the two monitors working, I get two clone screens with the resolution at 800x600 in both of them.

Does anybody know how to set both monitors at 1280x1024@75 as a spanned screen, where windows can be dragged from one to the other?
I hope someone could find an interesting and effective answer.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Since you have the restricted driver installed you need to:

```
sudo nvidia-settings
```

There should be a section on Twin View.  I run the 169.12 and Twin View was a snap.  The twin view allows you to set the resolution and which monitor in main.

---

### Post by csantama on 2008-04-15
I've run nvidia-settings but there's no solution to my problem. Both monitors work as clones and at 800x600 screen resolution. With no possibility to change the resolution nor make them work as a spanned screen

---

