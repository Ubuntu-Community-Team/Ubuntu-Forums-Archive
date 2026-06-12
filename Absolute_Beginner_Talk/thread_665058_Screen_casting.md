---
title: "Screen casting?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-11
I know screen casting is possible...but what software would you recommend? Is there a Linux version of Camstudio? I really like that software on my XP comp.

---

### Post by nikoPSK on 2008-01-11
screencasting can be done with gtk-recordmydesktop :KS

---

### Post by moebob24 on 2008-01-11
> **nikoPSK said:**
> screencasting can be done with gtk-recordmydesktop :KS

hmmm...ok does that launch on app or is it shell based

---

### Post by Hospadar on 2008-01-11
it's a terminal thing, you'd just open up a terminal window (Applications->Accessories->Terminal) and type recordmydesktop

There's some more command line options as well, try a "man recordmydesktop". to stop recording ctrl-C in the terminal window.

It records the videos in ogg format, so if you want to change them to something more common like xvid or mpeg you might want to use something like avidemux.

To install it, either use synaptic or do ```
sudo apt-get install recordmydesktop
```

---

### Post by nikoPSK on 2008-01-11
> **moebob24 said:**
> hmmm...ok does that launch on app or is it shell based

no theres a visual version.

---

