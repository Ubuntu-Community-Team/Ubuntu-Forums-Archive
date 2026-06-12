---
title: "kde only starts in safe recovery"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by alastair560 on 2007-02-17
Feeling a little lost and embarrased, I'm kind of okay with commandlines but basically a desktop person unless I'm forced into learning.
Okay I'm running ubuntu 6.06 Dapper on a 2.6 kernel. A friend donated this desktop to me with Ubuntu loaded. I installed kde and everything was working fine for a few weeks until I installed kubuntu-desktop.
Now it gets weird. I rebooted and got a black screen with a wee white box in the upper left hand corner with my login but no way of loging in. It seemed teh keyboard wasn't responding and now I think about it, the keyboard had weird mappings, backspace wasn't doing backspacing.
I managed to hit escape on pressing the reset button and got into safe recovery mode and managed to startx at a prompt. This got me into Gnome where I uninstalled kubuntu, not sure if that was a good idea but it was all I could think of. But when I rebooted, I got that same weird black screen. But it gets weirder.
I've found that typing kdm at a safe recovery prompt does nothing, gdm gets me into kde and startx gets me to gnome.
I absolutely love Linux, having migrated a couple of years ago but finding help can be hard, if anyone can help I would appreciate it. I can still use safe recovery for now but would like to fix so I at least  have a session choice at login.
Cheers,
Confused.

---

### Post by Jussi01 on 2007-02-17
Hmmm... dunno what went wrong, you could however try to reinstall gnome... 

```

sudo apt-get install gnome --reinstall
```

---

### Post by alastair560 on 2007-02-17
I will try that, should I try to reinstall kubuntu-desktop as well?

---

### Post by Jussi01 on 2007-02-17
JUst try gnome for now...

---

