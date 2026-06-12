---
title: "Wine + Steam (CSS) + WoW issue."
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by israfil334 on 2008-02-16
Hey guys, my first post here.
Just switched to Ubuntu last night and I'm tooootally loving it.
got compiz working n everything.

What I'm trying to do is have wine not run programs in a virtual desktop by default. But run some programs in a virtual desktop.

So basically I want steam to run regularly, and world of warcraft to run on a virtual desktop.

When I enable the virtual desktop from winecfg wow runs on a virtual desktop in fullscreen.
but when I tried wine explorer /desktop=1024x768 ~/.wine/wow/WoW.exe -opengl it started wow in the virtual desktop window but it was an actual window and not fullscreen.

Any help would be appreciated :)

---

### Post by Zalbor on 2008-02-16
In the first tab of winecfg, it has a list of programs that you can add to. If you want a program to have different options than the defaults, add it to the list and select it. The "Libraries" and "Graphics" tabs will be different for each program in the list, so with one selected go to Graphics and set different options.

---

### Post by israfil334 on 2008-02-16
> **Zalbor said:**
> In the first tab of winecfg, it has a list of programs that you can add to. If you want a program to have different options than the defaults, add it to the list and select it. The "Libraries" and "Graphics" tabs will be different for each program in the list, so with one selected go to Graphics and set different options.

Thanks good idea.
I added a Wow setting but now the "emulate a virtual desktop" checkbox is disabled

---

