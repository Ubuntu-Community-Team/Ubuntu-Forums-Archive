---
title: "Improve boot time"
date: 2007-08-30
forum: Apple PPC Users
---

### Post by stmiller on 2007-08-30
I just saw this thread:

[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

and you can do this with yaboot under PowerPC also. At the yaboot prompt where you most likely usually hit Enter, type in the 

**image label** *space* **profile**

For instance you would most likely type this at the yaboot prompt:
```

Linux profile

```

You only have to do this once. The first time it will take a long time as it builds the profile, but then just reboot as normal and you can verify the faster boot time. w00t!
If you are not sure of your default image label, just hit TAB at the yaboot prompt.

---

### Post by pxwpxw on 2007-08-31
computer-cpuspeed-ram, startup1-startup2, improvement secs.

iBookg4ppc-1Ghz-756Mb, 62-54, 8 secs
PC celeron-700Mhz-512Mb, 54-48, 6 secs
MacBook c2d-2Ghz-1Gb, 30-29, 1 sec
Profile run time was about 2 x startup.

All using wireless net, and xubuntu704, time to login.

Worth doing. Especially if  a lot of changes from initial profiling have increased startup time.

powermacG5sp-1.6Ghz-2.2Gb, 41-41, 0
ethernet network

---

