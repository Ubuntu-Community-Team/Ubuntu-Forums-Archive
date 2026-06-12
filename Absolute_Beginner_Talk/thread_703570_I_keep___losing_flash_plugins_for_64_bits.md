---
title: "I keep   losing flash plugins for 64 bits"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by sunseeker888 on 2008-02-21
HI GUys


I keep having problem with flash plugin player with Ubuntu 64 bits.

I keep removing plugin-non free with package manager, complete removal, then re-installed it again. The flash would work, then after a few session, I can't view the web page again, youtube [http://www.speedtest.net/](http://www.speedtest.net/) etc.


I have tried several things like complete removal, then go a webpage where they say plugin missing, add plugin, again it would work again, then revert back.


I have done this also
gksudo aptitude install flashplugin-nonfree

same thing happening, work then revert back


Also that tar.gz from Adobe does not work with 64 bits


Any Idea how I can force Ubuntu use that plugin:confused:

---

### Post by Vadi on 2008-02-21
Try this guide: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

It shows how to get 32bit firefox setup and plugins (java, flash) for it.

Just remember to use "firefox32" to launch firefox, because "firefox" will launch the 64bit one (that's after you've done the guide).

---

### Post by sunseeker888 on 2008-02-21
> **Vadi said:**
> Try this guide: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

It shows how to get 32bit firefox setup and plugins (java, flash) for it.

Just remember to use "firefox32" to launch firefox, because "firefox" will launch the 64bit one (that's after you've done the guide).



Thanks mate

---

