---
title: "Deskpop"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by WNATICAS74 on 2008-02-13
Help!   My friend mess with my PC   I noticed  that I don't have a menu, everything is gone. I've been putting the icons from add panels.   How do I reset to my original desktop?

:guitar:

---

### Post by Crooksey on 2008-02-13
From the terminal run..

```

rm -rf  ~/.gtk*
rm -rf ~/.gn*
rm -rf ~/.na*

```

That should delete all user created settings, for gnome, for kde..

```

rm -rf ~/.qt*
rm -rf ~/.kde*

```

---

