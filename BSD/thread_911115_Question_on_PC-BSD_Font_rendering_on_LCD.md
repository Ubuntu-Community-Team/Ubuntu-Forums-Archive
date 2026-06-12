---
title: "Question on PC-BSD Font rendering on LCD"
date: 2008-09-05
forum: BSD
---

### Post by kpkeerthi on 2008-09-05
Those who run Ubuntu (& Arch ;)) on a system with LCD monitor know already how good the fonts are rendered (with the clear-type patches to libxft, freetype & cairo packages). 

Can someone here running PC-BSD tell me how the font rendering is on LCD?

---

### Post by kpkeerthi on 2008-09-08
No PC-BSD users here?

---

### Post by mips on 2008-09-08
I used pcbsd on my laptop a long time ago and from what I recall the fonts were fine.

---

### Post by kpkeerthi on 2008-09-08
Thanks.

The latest PC-BSD looks cool. Although the default desktop environment is KDE, I might give it a whirl when the final is release.

---

### Post by LateNiteTV on 2008-09-10
try compiling print/freetype2 with WITH_LCD_FILTERING.

---

### Post by kpkeerthi on 2008-09-28
Tried PC-BSD. The default font rendering was terrible. Got the ports and compiled freetype with LCD filtering patch (Thanks LateNiteTv!). That made quite a huge difference. 
But I didn't quite like PC-BSD. The KDE4.1 was terrible and the DE crashed often - not sure what crashed but I ended up having a blank desktop consistently. Only a restart could fix it and but it kept on crashing. Wiped the partition clean after playing with it for a couple of hours. Couldn't stand it for long. Worst *NIX experience.

---

