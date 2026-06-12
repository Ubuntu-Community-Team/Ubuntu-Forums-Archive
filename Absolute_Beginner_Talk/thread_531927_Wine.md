---
title: "Wine"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by gaddo on 2007-08-22
Could someone  tell me what "wine"is and does and if needed where to i get it?
Thats

---

### Post by Amazona aestiva on 2007-08-22
Yuo can get Wine at in .deb [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html").

---

### Post by StooJ on 2007-08-22
Wine Is Not an Emulator.

[QUOTE=Wikipedia]Wine is a project which aims to allow a PC with an x86 architecture processor running a Unix-like operating system and the X Window System to execute programs that were originally written for Microsoft Windows. Alternatively, those wishing to port a Windows application to a Unix-like system can compile it against the Wine libraries in the form of Winelib[/QUOTE]

It's an effort to try and get Windows programmes working in Linux, I think it works using a port of DirectX, but I might be wrong.

Wine works for some things straight away, some things after a lot of tweaking, and some things not at all. 

[Rest of the wikipedia article]("http://en.wikipedia.org/wiki/Wine_%28software%29")

---

### Post by toidi on 2007-08-22
Wine lets you run windows programs on linux.  More info can be found at [www.winehq.org](www.winehq.org)

Easiest way to install wine in ubuntu is to open up a terminal/console and enter the following.

```
sudo apt-get install wine
```

This will download and install wine from the ubuntu repositories.

Once installed you should run wine configuration.
```
winecfg
```

There is lots of info on both these forums and at the winehq on how to configure and run wine.

---

