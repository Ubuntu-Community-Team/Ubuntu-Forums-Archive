---
title: "State of full screen magnification"
date: 2007-12-17
forum: Assistive Technology &amp; Accessibility
---

### Post by musther on 2007-12-17
At the moment I'm using the ezoom plugin for compiz for very flexible full screen magnification.  

In almost all respects this is really great, zoom to window size and things are just great.

The only problem is the lack of text cursor tracking - which is rather annoying.  But I've heard people talking about text tracking, with gnome-mag I believe.  Is this the only way to get cursor tracking?  

Also, if I try to start gnome-mag, for example like this:

magnifier -f -z 2

It doesn't work, the screen flickers, zooms for a moment, and then returns to normal with only this output:

```
(magnifier:6128): Bonobo-WARNING **: Assigning a default value to a non readable property 'source-display-screen'

(magnifier:6128): Bonobo-WARNING **: Assigning a default value to a non readable property 'target-display-screen'
** Message: added event source to xfixes cursor-notify connection
** Message: added event source to composite connection
initial viewport 1280 800
** Message: set source bounds to 0,0; 1280,800

```

So, is there any way to get the best of both worlds?

---

### Post by linbetwin on 2007-12-18
The easiest way to run gnome-mag is through orca. It has cursor tracking but unfortunately (for people who use high magnification factors) the cursor is not centered. Also gnome-mag uses quite a lot of CPU and RAM compared to ezoom.

Ezoom would be the perfect solution if it had cursor/caret tracking.

---

### Post by musther on 2007-12-18
I agree, compared to any other screen magnifier, it's system impact is very low, and it's performance is very high, it's just the tracking.

---

