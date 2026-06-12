---
title: "no close button"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-11-07
can anyone please help me? i installed compiz yesterday and today when i started my compouter..there were no close,max, min button.. plus there is no windows slecter.. i cant even do alt + tab.. i removed all the compiz using sypnatic .. but its still the same..can anyone please help me ? its weird i have opened like so many threads recently but none helps me :(

---

### Post by Dr Small on 2007-11-07
Have you tried:
```
metacity --replace
```

In the run dialog ?

---

### Post by HunkieChan on 2007-11-07
thanks a lot bro.. taht worked.. can i reinstall compiz now.. ?

---

### Post by MrFSL on 2007-11-07
I would suggest following the instructions found at:

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by mtngun on 2007-11-08
It appears that Compiz may disable the title bar on some systems, mine included.

There are some keystroke substitutes:

Maximize = alt + F10

Minimize = alt + F9

un-Maximize = alt + F5

Close = alt + F4

I found these by doing an advanced search in the desktop effects program.

---

### Post by MrFSL on 2007-11-08
> **mtngun said:**
> It appears that Compiz may disable the title bar on some systems, mine included.

There are some keystroke substitutes:

Maximize = alt + F10

Minimize = alt + F9

un-Maximize = alt + F5

Close = alt + F4

I found these by doing an advanced search in the desktop effects program.

I don't think that it is the case that it is being "disabled" so much as that the window manager is crashing (Emerald, gtk-window-decorator, etc.)

---

