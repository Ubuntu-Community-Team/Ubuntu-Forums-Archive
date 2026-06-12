---
title: "Enable just alt-tab preview?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by dmub82 on 2008-04-17
In System-Preferences-Appearance, I've set Visual Effects to none because I most of the window animations distracting and unnecessary, but I'd like to re-enable the Alt-Tab window previewing. Can I enable that effect by itself? What I'd really like is an "Advanced..." or "More Options..." button on the Visual Effects tab that would allow me to individually select options. (Running Gutsy, BTW). Thanks.

---

### Post by joshrobinson on 2008-04-17
> **dmub82 said:**
> In System-Preferences-Appearance, I've set Visual Effects to none because I most of the window animations distracting and unnecessary, but I'd like to re-enable the Alt-Tab window previewing. Can I enable that effect by itself? What I'd really like is an "Advanced..." or "More Options..." button on the Visual Effects tab that would allow me to individually select options. (Running Gutsy, BTW). Thanks.

you will have to re-enable the visual effects option, then install ccsm

```
sudo apt-get install compizconfig-settings-manager
```

run it with
```
ccsm
```
and disable the effects that you no longer want, leaving only the alt+tab switcher

---

### Post by dmub82 on 2008-04-17
Thanks. I got that set up and found the setting I want, think it was Application Switcher, but in the process I lost title bars on all my windows until I went back to None under Visual Effects.

---

### Post by angry_johnnie on 2008-04-17
You'll have to go back to ccsm, and enable **window decorations**

Metacity alone offers a somewhat similiar function.
Alt+Tab will let you switch windows, but it won't give you previews.  Only a small icon for each window.

---

### Post by joshrobinson on 2008-04-17
someone beat me to it, make sure window decorations is checked, if it still doesnt work let me know

---

