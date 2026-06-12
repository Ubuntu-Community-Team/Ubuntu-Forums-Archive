---
title: "Kubuntu 6.10 disabling spell checking globally"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by monkman on 2007-02-20
hello.

how can i disable the annoying spell checking? i just find the possibility to change the "engine" but not to stop it.

thx!

---

### Post by NewOldTimer on 2007-02-20
checking
You know that ? You are writing a text in your webbrowser and suddenly, some words get red and black again, or they stay red. This is as-you-type spell checking. You can disable it by adding

KSpell_DoSpellChecking=0


in the KSpellexternal link section of your ~/.kde/share/config/kdeglobals. You need to restart konqueror afterwards. See also [http://bugs.kde.org/83423.external](http://bugs.kde.org/83423.external) link


Taken from  [http://wiki.kde.org/tiki-index.php?page=Tips](http://wiki.kde.org/tiki-index.php?page=Tips)    hope it helps

---

