---
title: "Mercury messenger grey window"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-17
I installed mercury messenger to try it out, and everything seems to be working properly, except when I launch it. It launched find with the load meter and stuff, but once its done the window comes up. The window is just the title bar, with a grey window frame where the contents should be.

I am running Beryl/XGL which may have something to do with it.

If anyone knows how to fix this, it would be really appreciated. 

Thanks. 

-Skyler

---

### Post by CyberAngel on 2007-01-21
The problem is from beryl for sure...
I am using Mercury messenger too without any problems but when I am starting beryl-manager I have the same problem as you described...

If anyone knows something more please help :)

---

### Post by CyberAngel on 2007-01-21
Exactly the same problem using matlab.....

Maybe the problem has to do with beryl + java combination :(

---

### Post by Skyler0 on 2007-01-21
I can't remember exactly how I fixed it (sorry lol), but you have to disable the systray icon. I think on the FAQ on the site it says how to do it or something. But I need the systray so I'm not using it nemore lol

---

### Post by CyberAngel on 2007-01-21
From Mercury FAQ:
> Beryl / Compiz Java Bug

If you are running Beryl/Compiz and start Mercury, you might see a blank windows, this is a java bug (Sun 1, Sun 2, Beryl).

There are a few workarounds, the easiest to try is typing export AWT_TOOLKIT=MToolkit before typing mercury. It might crash because the tray icon library doesn't support this toolkit, you can prevent the crash by renaming/removing jni/linux/libtray.so. 

Thanks! But it is not so useful without the tray icon so I will just not use Mercury with Beryl at the moment :)

As it says it is a Java bug so that`s why matlab doesn`t working too.

---

