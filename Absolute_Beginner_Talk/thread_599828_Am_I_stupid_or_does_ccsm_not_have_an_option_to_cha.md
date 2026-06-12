---
title: "Am I stupid or does ccsm not have an option to change your theme?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jawknee530 on 2007-11-01
I want to change my desktop theme in 7.10 and have compiz-fusion installed.  i cant find anything in ccsm to do this.  can anyone direct me to it?

---

### Post by llamakc on 2007-11-01
You're correct. There's nothing in there.

You change the theme in System | Preferences | Appearance, or with whatever theme-manager Emerald offers if you use Emerald.

---

### Post by jawknee530 on 2007-11-01
is emerald compatible with compiz?  how do i get it?

---

### Post by llamakc on 2007-11-01
Yes, you install it from the repositories. Search in Synaptic for it.

---

### Post by Hospadar on 2007-11-01
you can install "emerald" from synaptic and then you can download and use emerald themes.

You'll need to change compiz so emerald is the window decorator, from a terminal:```
compiz --replace emerald
```

You might want also to poke into the fiesty repositories and grab the old emerald-themes package to get some standard emerald themes (emerald by default comes with no themes)

---

