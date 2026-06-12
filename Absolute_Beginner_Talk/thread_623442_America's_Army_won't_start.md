---
title: "America's Army won't start"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by crav on 2007-11-25
I installed and all, and I get the following error when running from terminal:

```

*me*@*mycomputer*:~/armyops$ sh ./armyops 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error

```

---

### Post by Majorix on 2007-11-25
Seems like you don't have 3D acceleration. Can you post the output of
```
glxinfo | grep rendering
```
to make sure?

---

### Post by crav on 2007-11-25
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

If it helps (or hurts) I have an ATi Radeon Xpress 200M

---

### Post by Majorix on 2007-11-25
I hear you. I have an ATI card too :)

Anyways try the second post here and see if it fixes it for you:
[http://ubuntuforums.org/showthread.php?t=292642&highlight=Xlib%253A+extension+XFree86-DRI%2526quot%253B+missing+on+display+%2526quot%253B%253A0.0](http://ubuntuforums.org/showthread.php?t=292642&highlight=Xlib%253A+extension+XFree86-DRI%2526quot%253B+missing+on+display+%2526quot%253B%253A0.0).

---

