---
title: "Square Cursor in Wine - Kubuntu/Ubuntu Gutsy"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jdlongmire on 2007-12-15
have not seen this in any WIne install on Kubuntu - done it about 5 times with Gutsy - but my mouse arrow is this .5"x.5" square box with black and white alternating lines. The upper right corner of the box works as the arrow tip, but it is very distracting - any help?

I have been ALL OVER google - no joy :(

---

### Post by MethodOne on 2007-12-16
Do you have a Matrox video card? Other cards might experience this problem too.  You have to add a line to /etc/X11/xorg.conf to get rid of the square cursor. To do so run the following:

```
kdesu kate /etc/X11/xorg.conf
```

Then add this line at the end of the "Device" section (case sensitive):

```
Option "HWCursor" "off"
```

and save the file. Save your work, press Ctrl+Alt+Backspace, log back in and launch the application you wanted.  That will return the cursor to normal.

---

