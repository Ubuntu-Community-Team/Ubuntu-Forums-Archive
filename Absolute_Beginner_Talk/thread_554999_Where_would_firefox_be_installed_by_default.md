---
title: "Where would firefox be installed by default?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-09-19
I need to find where it was installed. Just tell me where it would be located as if it were a fresh install of Ubuntu. Thank you in advance.

---

### Post by mysticmatrix on 2007-09-19
> **dljesse said:**
> I need to find where it was installed. Just tell me where it would be located as if it were a fresh install of Ubuntu. Thank you in advance.

Executable in /usr/bin
Docomentation in /usr/doc
Default settings and themes under /usr/share

and many other places.

Your personal setting are under /home/<username>/.mozilla/firefox

EDIT: Forget to point out, but you can open Synaptic, search for firefox package, and right click to view where all files are installed.

---

### Post by yabbadabbadont on 2007-09-19
/usr/lib/firefox is the program directory.  There will be links/startup scripts in /usr/bin.

---

### Post by jordanmthomas on 2007-09-19
The executable can be found by typing:
```
which firefox
``` in a terminal.  It should be /usr/bin/firefox I think but my distro has it in /opt so I can't tell you for sure.

The libraries associated with firefox will be in /usr/lib/mozilla/firefox or /usr/lib/firefox
Your configuration for firefox will be in ~/.mozilla/firefox

Also, you can use Synaptic to view all the files firefox has installed on your system.

**edit** wow, you got attacked by answers, didn't you?

---

### Post by dljesse on 2007-09-19
Thanks guys.

---

### Post by mysticmatrix on 2007-09-19
> **yabbadabbadont said:**
> /usr/lib/firefox is the program directory.  There will be links/startup scripts in /usr/bin.

Doesn't /usr/lib/ usually stores development files needed for compilation of programs?

---

### Post by jordanmthomas on 2007-09-19
It contains libraries needed for runtime stuff mostly.
The headers you are thinking of are the ones in /usr/include maybe?

---

