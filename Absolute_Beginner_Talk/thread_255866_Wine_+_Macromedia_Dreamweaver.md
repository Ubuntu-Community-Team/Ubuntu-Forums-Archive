---
title: "Wine + Macromedia Dreamweaver"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Peterchen Brot on 2006-09-12
Hi,

i tried to install Dreamweaver with wine (wine /path/dreamweaver8.exe). But it stopps during the install process. What can i do?

---

### Post by ser1alsn1per on 2006-09-12
[http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)


try this



remember google is your friend

---

### Post by Peterchen Brot on 2006-09-12
I already googeled.

But i habe no windows installed. I change my wine version and configured it with winetools. internet explorer(for e.g.) works.

But when i try to install dreamweaver it told me that my windows installer version ist to old. When i try to install a newer version it told me that 

"Unable to find a volume for file extraction. Please verify that you have proper permissions."

---

### Post by RobsterUK on 2006-09-13
I tried the tutorial above and it didn't work. So I ended up using [Crossover Linux]("http://www.codeweavers.com/products/cxoffice/")
Worth noting that its about $40 after a 30 free trial but so far for me it runs Dreamweaver perfectly.

---

### Post by simone.brunozzi on 2006-09-15
40 dollars, not 30.
Anyway, Crossover is a proprietary software, and thus has a potential security issue built-in :-)
I can understand you wanted a quick solution.

---

### Post by simone.brunozzi on 2006-09-15
I followed the instructions for wine + dreamweaver, however, when I run "wine dreamweaver.exe" I get the following warning, and then the program say there is a problem and quit. Here is the warning:

```
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7d0,0x00000000), stub!

```

Any hints?

---

