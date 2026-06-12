---
title: "MacBook Pro, ATI X1600 performance in Maya, Ubuntu 8.04"
date: 2010-11-09
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-11-09
Hi,
On a MacBook Pro (Core Duo, 2.16, ATI X1600, 2006), I have the latest ATI fglrx drivers (Catalyst 9.3) installed under Ubuntu 8.04. It all seems to be good. However my OpenGL performance is really messy. I get all kind of refresh problems (black areas, broken GUIs etc.) while working in Maya 2008.

I think I need to edit my xorg file? And chnage something realted to something called "compiz"?

Any good resources on how to optimize my OpenGL performance.

Thanks.

---

### Post by Symbolix on 2010-11-09
Agggrrr!! All this ATI Catalyst s**t, Kernels, Libs, GCCs! This is just ruining my life :) It should not be that hard!

I am stuck with this crap.

---

### Post by Symbolix on 2010-11-10
Any ideas?
:(

---

### Post by Symbolix on 2010-11-11
Heeeeelp!? :(

---

### Post by linuxopjemac on 2010-11-11
maybe Google a little?
[http://ohioloco.ubuntuforums.org/showthread.php?t=485309](http://ohioloco.ubuntuforums.org/showthread.php?t=485309)

[http://webcache.googleusercontent.com/search?q=cache:gEfCo7LmPD4J:wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide+cchtml+wiki+feisty&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:gEfCo7LmPD4J:wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide+cchtml+wiki+feisty&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

[http://peterchuang.com/blog/2008/09/77/](http://peterchuang.com/blog/2008/09/77/)

---

### Post by Symbolix on 2010-11-11
Thanks! Sorry for being a pain. I checked google, but there is so much stuff, hard to filter without any initial experience. Your links are helpful. Will try them at home.

(I so much want to get my hands on some of those new MacBook Pros, but this will never happen, so expensive! - An nvidia hardware would make my life so easy)

I need to get my old mac stable as soon as possible, and I am getting furstrated by the fact that it is not happening :( )

Thanks.

---

### Post by Symbolix on 2010-11-12
Thanks!

I added this to the end of my xorg file:

```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

OpenGL works much better now. Not very fast but at least stable and all the windows draw and update properly.

Cheers.

---

### Post by linuxopjemac on 2010-11-12
Great!

---

