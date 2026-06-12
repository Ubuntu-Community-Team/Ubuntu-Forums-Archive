---
title: "Not able to put &lt;tk&gt; on Ubuntu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by noe287 on 2007-03-26
Hi all,

     I am new to Ubuntu and trying to install tk8.4.14 on on gcc:

            "Using built-in specs.
            Target: i686-pc-linux-gnu
            Configured with: ./configure 
            Thread model: posix
            gcc version 4.1.2"

   but i get this error:


*
*
*

   /home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1206: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1211: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1218: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1220: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1222: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1229: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1231: error: invalid type argument of ‘->’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c: In function ‘Tk_Get3DBorderFromObj’:
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1264: error: ‘TkWindow’ has no member named ‘dispPtr’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1279: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1280: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1280: error: ‘TkBorder’ has no member named ‘screen’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1281: error: ‘Tk_FakeWin’ has no member named ‘atts’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1281: error: ‘TkBorder’ has no member named ‘colormap’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1301: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1306: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘display’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1307: error: ‘Tk_FakeWin’ has no member named ‘screenNum’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1307: error: ‘TkBorder’ has no member named ‘screen’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1308: error: ‘Tk_FakeWin’ has no member named ‘atts’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1308: error: ‘TkBorder’ has no member named ‘colormap’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1311: error: ‘TkBorder’ has no member named ‘objRefCount’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c: In function ‘TkDebugBorder’:
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1391: error: ‘TkWindow’ has no member named ‘dispPtr’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1394: error: ‘TkDisplay’ has no member named ‘borderTable’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1400: error: ‘TkBorder’ has no member named ‘nextPtr’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1403: error: ‘TkBorder’ has no member named ‘resourceRefCount’
/home/noe/dot31Ns/tk8.4.14/unix/../generic/tk3d.c:1405: error: ‘TkBorder’ has no member named ‘objRefCount’
make: *** [tk3d.o] Error 1

   any idea what it might be caused by? I just installed gcc since ubuntu didn't seem to have one by default on it. Thank for any help.

Noe

---

### Post by noe287 on 2007-03-26
Ok I found the problem. It was because default ubuntu lacks X11 graphics libraries where tk has a lot of references for. So i just launched the synaptic and downloadedall X11 related stuff, now it compiles! Thanks in any way.

Noe

---

### Post by cowlip on 2007-03-26
ubuntu up to Feisty Fawn doesn't have the build-essential metapackage installed by default, so try installing that, not just gcc.

otherwise,the packages  tk8.4-dev and tk8.4 from the Ubuntu repositories in Feisty are the latest, 8.4.14

---

