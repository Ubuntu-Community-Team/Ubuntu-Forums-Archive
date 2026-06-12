---
title: "Desktop Effects"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by DrBeaverhausen on 2007-04-24
OK, so I finally got to upgrade to 7.04 today.  And the desktop effects worked without doing any tweeking.  But for some reason the "cube" effect has stopped.  Everytime I try to restart it, it clears my workspace switcher.  Any ideas on how to get it going again?

---

### Post by jhnthn on 2007-04-24
Type this in the terminal
```
gconftool --type int --set /apps/compiz/general/screen0/options/hsize 4
```

---

### Post by Chamelion on 2007-05-16
jhnthn also a big thanks from me. I just installed the 3rd party pluggins for Compriz and lost my 3d and only had 1 desktop left. This did the trick.:)

---

### Post by JOrtiz8612 on 2007-05-16
> **Chamelion said:**
> jhnthn also a big thanks from me. I just installed the 3rd party pluggins for Compriz and lost my 3d and only had 1 desktop left. This did the trick.:)

Same here but I fixed it.

---

