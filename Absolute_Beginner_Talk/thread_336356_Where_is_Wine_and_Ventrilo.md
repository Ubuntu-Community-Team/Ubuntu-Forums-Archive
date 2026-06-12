---
title: "Where is Wine and Ventrilo?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by usersock on 2007-01-11
I installed Wine from Synaptic and then installed Ventrilo via wine. I'm having some problems.. I cannot open wine and I can't open Ventrilo, or even find either application folder. I have tried opening both with "run application" but had no luck. I'm not sure what else to do :-?

---

### Post by Qrk on 2007-01-11
Wine doesn't run by itself... think of it as a way to trick windows programs into thinking that they are running on windows, not as a separate application. First you should configure wine to work by running the programs winecfg.

```
winecfg
```

This makes a wine folder in your home directory that pretend to be drive C in windows. (its under ~/.wine )

Next you'll need to install the Microsoft programs that wine doesn't include. Things like install shield and the ilk... wine doesn't include them. You can get these by downloading winetools. However, winetools is not included the repositories, so go to [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

