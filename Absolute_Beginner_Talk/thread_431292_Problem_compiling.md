---
title: "Problem compiling"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by WanderingKnight on 2007-05-02
I'm trying to compile the snes9x source code. ./configure is ok, but when I input make, I got the following errors:

> In file included from unix/x11.cpp:180:
unix/x11.h:171:33: error: X11/extensions/XShm.h: No such file or directory
unix/x11.h:224: error: ‘XShmSegmentInfo’ does not name a type
unix/x11.cpp: In function ‘void S9xDeinitDisplay()’:
unix/x11.cpp:331: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:331: error: ‘XShmDetach’ was not declared in this scope
unix/x11.cpp:334: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:335: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:336: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:337: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp: In function ‘void SetupImage()’:
unix/x11.cpp:730: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:730: error: ‘XShmDetach’ was not declared in this scope
unix/x11.cpp:733: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:734: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:735: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:736: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:752: error: ‘XShmQueryVersion’ was not declared in this scope
unix/x11.cpp:755: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:756: error: ‘XShmCreateImage’ was not declared in this scope
unix/x11.cpp:764: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:767: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:775: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:775: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:780: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:785: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:788: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:788: error: ‘XShmAttach’ was not declared in this scope
unix/x11.cpp:797: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp:798: error: ‘struct GUIData’ has no member named ‘sm_info’
unix/x11.cpp: In function ‘void Repaint(bool)’:
unix/x11.cpp:1245: error: ‘XShmPutImage’ was not declared in this scope
make: *** [unix/x11.o] Error 1

Any suggestions?

---

### Post by jfinkels on 2007-05-02
> **WanderingKnight said:**
> I'm trying to compile the snes9x source code. ./configure is ok, but when I input make, I got the following errors:



Any suggestions?

If you don't figure it out, you can always install it from the repos (i.e. use Synaptic).

---

### Post by yabbadabbadont on 2007-05-02
Go to the project's website and make sure that you have the development versions of all of the listed build dependencies installed.  For the specific error you listed, you probably need to install the xorg-dev package.

---

### Post by WanderingKnight on 2007-05-02
Thanks a lot. I'm definitely a newbie to all this stuff-I'm on my 4th day of Linux. Guess I'll get used to it someday.

---

### Post by macogw on 2007-05-02
Why are you compiling if you're so new to it?  Compiling is advanced.  Use Synaptic or the Add/Remove thing to do it.  That way's much easier.

---

