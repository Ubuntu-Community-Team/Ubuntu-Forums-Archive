---
title: "Any reason in particular why FF operates slowly all of a sudden?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ogwilson on 2007-11-02
For some reason, everything jut got slower a couple days ago. I can barely scroll down a web page without it hiccuping, the shutdown/startup time is like 3 minutes now, and to start a program, i have to walk away for a while because my CPU is being thrown into a woodchucker it seems.

---

### Post by agurk on 2007-11-02
Hard to say, it could be a million things I guess, but for starters, see if you can find any suspect(s) by observing System-->Administration-->System Monitor.

---

### Post by philinux on 2007-11-02
One culprit - trackerd

---

### Post by alienexplorers on 2007-11-02
Check out these extensions that cause problems with Firefox:
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by Adramelech on 2007-11-02
or use synaptic to install htop, and use it to see what process is eating your memory and/or your processor

---

### Post by ogwilson on 2007-11-02
Thanks all for the timely responses! I'll try those programs and see wwhats going on.

---

### Post by mivo on 2007-11-02
Type *about:config* in the URL field, and enter *network.dns.disableIPv6*. Click on the value and toggle it. See if it helps. :)

If all else fails, you can delete the hidden .mozilla folder in your home directory (try renaming it first to see if it helps). Backup your bookmarks in any event.

---

