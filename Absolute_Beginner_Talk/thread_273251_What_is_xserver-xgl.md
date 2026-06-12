---
title: "What is xserver-xgl?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-07
I hear xgl here and there on the forums and I have the package xserver-xgl in the repos. What is it really? how does it work? :D

---

### Post by jordanmthomas on 2006-10-07
How XGL works (complicated) -- [http://www.freesoftwaremagazine.com/articles/accelerated_x](http://www.freesoftwaremagazine.com/articles/accelerated_x)
It compares AIGLX and XGL

Basically, XGL runs on top of a standard X server and can intercept the drawing of elements on screen, which it can then pass off to the graphics card.  If you just install xserver-xgl, nothing will happen.  You need to a) enable it and b) use a window manager that takes advantage of the extra features.

If you're interested, you may want to check out compiz, a window manager that uses an accelerated x-server
(I'd suggest beryl, though, it's compiz on steroids)

Hope this helps somewhat

---

### Post by WalmartSniperLX on 2006-10-07
Thanks :D

---

