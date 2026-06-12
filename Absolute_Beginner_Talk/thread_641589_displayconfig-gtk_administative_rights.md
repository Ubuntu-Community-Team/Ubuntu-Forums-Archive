---
title: "displayconfig-gtk: administative rights?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by cyclingman on 2007-12-15
After wanting to attach an external monitor onto my dell laptop via my s-video port, I noticed the "displayconfig-gtk" program was installed (after i looked in synaptic). When i try to boot this program, either from the terminal or using from my menu bar I am prompted with:

"You need administrative rights to change all screen settings"

I'm not sure what this means, as I AM logged in as administrator and have previously just been given the option to enter my passwords when opening any other administrative program, but am not with this:(.
        I am allowed to look at the program but cannot change any settings either on; screen 1, screen 2, or graphics card.

Help is much appreciated :KS

(P.S. sorry if this is a very simple question but I am an absolute beginner)

---

### Post by cyclingman on 2007-12-15
anyone?

---

### Post by jken146 on 2007-12-15
If you need administrative rights to run a program, you must preface the command with 'sudo' or 'gksudo'.  E.g.
```
sudo apt-get install <package>
gksudo nautilus
```

Usually the shortcuts in the menus handle this for you (e.g. when you start Synaptic), but this may not always be the case when you install something yourself, unfortunately.

---

### Post by cyclingman on 2007-12-16
wahoo, thank you for that simple answer, i have just furthered my ubuntu knowledge :)

---

