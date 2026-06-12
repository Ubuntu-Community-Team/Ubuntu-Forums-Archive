---
title: "XMMS freezes entire system when attempting &quot;double size&quot;"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
Every time I open XMMS and attempt to change the view to Double Size (Right click - Options - Double Size) it freezes the entire computer. I checked out this thread ([http://ubuntuforums.org/showthread.php?t=268577](http://ubuntuforums.org/showthread.php?t=268577)) but that isn't exactly what's happening with mine - it just freezes the entire system.

Does anyone have any idea why this is happening? Thanks in advance for any insight!

---

### Post by Pragmatist on 2007-08-06
According to this thread, 
[http://osdir.com/ml/user-groups.linux.cabal/2006-12/msg00216.html](http://osdir.com/ml/user-groups.linux.cabal/2006-12/msg00216.html)

you can try typing this in a terminal:
```
*[I]'export XLIB_SKIP_ARGB_VISUALS=1 && xmms'*[/I]
```

However, I don't know if that will affect any other programs.

---

