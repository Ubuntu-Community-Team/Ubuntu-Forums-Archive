---
title: "Divx kills itself?"
date: 2008-02-21
forum: Apple PPC Users
---

### Post by googlegot on 2008-02-21
about 1 minute after starting any divx video in any movie player on my imac g4, the video will just quit out, no error, nothing in dmesg, it just disappears like it was never running in the first place.  Anyone have an idea of how to fix this issue?

---

### Post by BladeMelbourne on 2008-02-21
Which video players(s) are you using?

Have you tried VLC (videolan client)? Does it behave the same way?

If it does, whichever player you use, go into the video output preferences and change the output driver from xv (also known as xvideo) to 'x11 video output'.

Let us know how you go...

---

### Post by googlegot on 2008-02-21
ive used mplayer vlc and totem, all with all the different output modules.  every single time it crashed, and any other file type plays no problem....except flash...damn adobe!

---

