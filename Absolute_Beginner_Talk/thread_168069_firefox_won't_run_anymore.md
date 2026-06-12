---
title: "firefox won't run anymore"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by ukemike on 2006-04-29
I just re-installed breezy and then ran Automatix.  I belive I selected the option to install FF1.5.  Anyway now FF just won't start.  Starting it from the app menu I get a tab saying "starting firefox" then it goes away.  Starting it from bash I get this error:

/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I've used synaptic to uninstall it and re-install it to no avail.

I'm using Opera right now, but I'm pretty partial to FF.

---

### Post by cilynx on 2006-04-29
The older version of FF that you're trying to run requires an older libstdc++ than normal.  If you install the libstdc++5 package, you should be fine:

```

sudo apt-get install libstdc++5

```

...or use Synaptic to install it if that works better for you

---

### Post by ukemike on 2006-04-29
Well I'll be...

That was easy, elegant, and obvious.  I'm even begining to understand how you got to that conclusion from the error message.  I'm really starting to like this (I figured I would)  Hell I may even build my next computer around some linux.

Thank you so much for the rapid and spot on help.

---

### Post by cilynx on 2006-04-29
As an aside, (no bad feelings towards automatix at all, I'm not familiar with it, but I hear good things) you can always get yourself the newest version of FF installed natively (as opposed to in /opt/ as your post shows) by doing:
```

sudo apt-get install firefox

```
This method will automagically install all of the dependencies as well.

NP on the help.  I try to dispell the Linux-Zealot myths whenever I can.  Glad to hear you're starting to get the system down.  Best of luck.

---

