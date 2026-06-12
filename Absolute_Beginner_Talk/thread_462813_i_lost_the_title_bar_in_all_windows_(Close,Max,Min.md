---
title: "i lost the title bar in all windows (Close,Max,Min)"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-03
I installed beryl on fiesty with nvidia 6150 after upgrading to nvidia-glx-new and the emerald themes are not working and I dont have the decoration, I guess that is what it is called.  I have a check in beryl for decorations.

Any help?

---

### Post by Ek0nomik on 2007-06-03
Try running:

```
beryl-manager
```

---

### Post by Ek0nomik on 2007-06-03
Also, this may help:

[http://ubuntuforums.org/showthread.php?p=2547338](http://ubuntuforums.org/showthread.php?p=2547338)

---

### Post by Tux Aubrey on 2007-06-03
There seem to various versions of this problem.  The one I had was solved by adding this line:

>     Option         "AddARGBGLXVisuals" "True"

to the "Screen" Section in xorg.conf (which holds the current record as the File Most Likely To Give Me Grief).

---

