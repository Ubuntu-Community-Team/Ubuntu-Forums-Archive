---
title: "Little tiny xgl issue"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by S{yndrom}e on 2006-06-13
Hi sorry to waste everyone's time.

My question is just a little one; I installed Xgl/compiz (and abosulutly love it) and its working fine and everything. It is just that now i want to do something requiring me to use Direct Rendering and OpenGL, which isnt supported in Xgl.

The problem is that everytime i login, Xgl is in the process list (which i suppose) doest allow me to perform OpenGL operations. The sscript that starts Xgl/compiz isnt located in the startup programs.

I was wondering if anyone could tell me how to (temporarily) remove xgl.

---

### Post by uzi09 on 2006-06-13
are you using XGL for nvidia or ati?

try searching this thread for xgl, you should be able to find all answers here:
[http://ubuntuforums.org/showthread.php?t=148351&highlight=aiglx+xgl+compiz+thread](http://ubuntuforums.org/showthread.php?t=148351&highlight=aiglx+xgl+compiz+thread)

i personally used aiglx, and for it the website ([http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)) says:
> 
4. Compiz-aiglx start script
the compiz-aiglx start script is now in package and automatically started on all gnome session startup. If you have some trouble with it you can remove compiz-aiglx.desktop file in /etc/xdg/autostart.


you actually do NOT have to delete the file (in fact, i'd recommend not doing it). if you open the file, you can disable the autostart -- there is a command there for that.

but since i don't know if the setup is the exact same or not, i'd recommend searching through that thread i provided first!

---

