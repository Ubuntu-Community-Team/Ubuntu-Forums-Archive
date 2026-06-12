---
title: "Why does my screen go dim and normal, dim and normal?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mikebravo on 2008-02-26
I do NOT have a laptop. I am running 7.10 on a desktop with 1 gig memory, core2Duo 2.33 gHz processor and GeForce8500 video card.  Everything has been perfectly normal, but the first time I went to    [http://www.harbornet.com/folks/rellis/MACHLISTSort.htm](http://www.harbornet.com/folks/rellis/MACHLISTSort.htm)  I got a blank page and then my screen started to slowly alternate between normal brightness and a dim gray.  After a long while the page finally appeared and was normal.  The web page is 9 or 10 screens long, of a spread sheet showing dog agility champions by breed.

I called up the System Monitor and watched the Resources tab while I redid the download. Network Activity peaked briefly (I have broadband) and went to nothing, however for at least three minutes the CPU Usage would alternate with one core at 100% and the other at almost nothing. Sometimes the alternations would be every two or three seconds and other times one core would carry the load for 15 to 20 seconds.  All during this time my screen would randomly fade to dim and return to normal.  Change in screen state seemed to correlate with the longer periods of CPU change but I cannot be sure.   Can someone tell me what is going on here?

---

### Post by Iehova on 2008-02-26
Are you running compiz (or 'desktop effects'? Does this only happen with one window at a time or the whole screen? Compiz will dim a non-responsive window to grey, and then tends to bring it back once it's sorted. This tends to happen every so often on firefox when loading large webpages.

---

### Post by Afkpuz on 2008-02-26
thats firefox thinking.  When it thinks for a long time, the system thinks that the window is hanging.  One of my annoyances with 7.10.

---

### Post by dlastik on 2008-04-14
> **Afkpuz said:**
> thats firefox thinking.  When it thinks for a long time, the system thinks that the window is hanging.  One of my annoyances with 7.10.still does this with 8.04.  does anyone know of a work around or perhaps a way to disable this pesky feature?

---

### Post by alexei.colin on 2008-05-02
Google found this at the location below:
"'general options -> ping delay' determines the delay when compiz greys out an unresponsive window. One can change that within a certain time range but, as far as I can find out, there is no way to switch it off."

[http://forum.compiz-fusion.org/showthread.php?p=32087]("http://forum.compiz-fusion.org/showthread.php?p=32087")

This might be an acceptable workaround.

---

