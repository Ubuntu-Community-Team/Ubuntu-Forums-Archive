---
title: "Ubuntu restarts using firefox"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-06-25
Ubuntu shuts down and sends me back to the login screen while using firefox.  Usually this happens after I've clicked to open a link in a new tab.  The new links do not seem to have anything in common.  I've seen mentions of issues with flash, but the pages that have caused crashes do not tend to be pages with flash on them.  Also, it's not consistent, some pages will cause multiple crashes in a row, and then load fine on the third restart.  

I'm using Fiesty, and  version 2.0.0.4 of Firefox.  

I'm sure you probably need more info than this, but I don't know what you'd need to know.  I'd love your help though and will provide any info I can.

---

### Post by Seisen on 2007-06-25
Do you  have any extensions installed.

Try opening up firefox in safe-mode

```
firefox -safe-mode
```

---

### Post by FurryNemesis on 2007-06-25
I had this issue using Firefox 2.0.0.2 - I upgraded to 2.0.0.3 and it went away. See if that version works better, and as a workaround if it doesn't, why don't you try Opera or Konqueror in the meantime?

---

### Post by nothinghead on 2007-06-25
I have a number of extensions installed

Adblock
Adblock Plus
Chatzilla
Conquery
Download Statusbar
and Greasemonkey which I'm only running one script on, page-specific, and not one of the pages that has ever caused a crash thus far

---

### Post by nothinghead on 2007-06-25
I was beginning to think that the problem was caused by stress on my connection (too many tabs loading at once) but I just had it kick me out to the login screen when closing a tab (and while nothing was loading).

---

### Post by Golyadkin on 2007-06-25
Have you tried disabling Greasemonkey? And then restarting the browser. Doesn't firefox create a logfile?

---

