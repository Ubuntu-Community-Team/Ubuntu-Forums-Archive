---
title: "keybindings on an ibook g4"
date: 2005-11-14
forum: Apple PPC Users
---

### Post by hatefulthreatening on 2005-11-14
I'd like to make my capslock a control button. I'd also like to bind the left apple button to control and the right apple button to alt. Is this possible?

I tried to make capslock a control in the kde settings menu, but this didn't work on my ibook as it did on my x86 desktop.

---

### Post by lixus on 2006-02-21
check "man xmodmap" and  run

```
xmodmap -pke > ~/.xmodmaprc
```

make changes to that file and
load it from ~/.xinitrc by adding a line like

```
xmodmap ~/.xmodmaprc
```

---

### Post by bennyp on 2006-06-15
How can I enable the apple keys for configuration with xkeycaps - which layout should I use?

---

