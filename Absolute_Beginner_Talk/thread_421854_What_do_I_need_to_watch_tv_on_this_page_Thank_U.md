---
title: "What do I need to watch tv on this page? Thank U"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by bucium on 2007-04-24
Hello!
Please tell me what do I need to watch tv on this page:
[http://www.realitatea.net/playlive2.php?live](http://www.realitatea.net/playlive2.php?live)
I had ubuntu 6.10 and I upgraded to 7.04. I never succeeded watching this tv program. HELP!:D

---

### Post by orb9220 on 2007-04-24
Totem Browser plugin.

But it doesn't work due to other sites like this one, I have to cross my fingers if totem plays a site or not.

Due a search on totem in forums to see if anyone has suggestions.

---

### Post by yabbadabbadont on 2007-04-24
mplayer firefox plugin should handle it.  It is a standard windows mms stream.  I looked at the page info and found the stream.  Then, in a terminal, I ran ```
mplayer mms://85.186.156.239
``` and it played fine.  I do have the win32codecs installed though, so you may need them too.

Edit: here is the information on the stream that mplayer displays
```
ASF file format detected.
VIDEO:  [WMV2]  352x288  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Realitatea LIVE
 author: LIVE
 copyright: Realitatea TV
 comments: Casa Presei Libere

```

---

