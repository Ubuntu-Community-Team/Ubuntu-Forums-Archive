---
title: "help! how to remove/uninstall window managers"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by LinuxSoundMan on 2007-11-17
through all my pain and struggle trying to find the best DE i finally have arrived at XFCE and i must say it fits my needs perfectly. now my only problem is i have 2 other window managers that i would like to remove. fluxbox and openbox. is there a simple command i can use to remove them as well as all of their "recomended" packages and components. when installing them i also apt-get installed the "recommended packages listed when you install the main package. if anyone has any advice id love to hear from you. thanks in advance.

---

### Post by philinux on 2007-11-17
Just uninstall from synaptic, mark for complete removal.

---

### Post by jken146 on 2007-11-17
```
sudo aptitude remove fluxbox openbox
```

---

### Post by LinuxSoundMan on 2007-11-17
'will this remove the "suggested packages" as well because i manually installed them after installing the main package.

---

### Post by jken146 on 2007-11-17
It will remove dependencies.  As for anything you installed separately you'll need to mark those for removal too.

---

### Post by LinuxSoundMan on 2007-11-17
thanks a lot for the info. kind regards.

---

### Post by urukrama on 2007-11-17
You've probably removed it already, but just to educate you: aptitude (not 'apt-get') checks for unused packages everytime it is run, so if you remove openbox or fluxbox with it and it installed dependencies with it that are not used by any other applications, you can remove them as well.

---

