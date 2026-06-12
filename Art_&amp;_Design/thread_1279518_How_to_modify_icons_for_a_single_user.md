---
title: "How to modify icons for a single user?"
date: 2009-09-30
forum: Art &amp; Design
---

### Post by Vaphell on 2009-09-30
I'd like to replace some icons in few apps - for example in pidgin and fast-user-switcher. I know their location in /usr/share, but the problem is that with every update they are overwritten by the default ones and i have to restore them.

I'd like to override system wide icons with few placed somewhere in my home directory. Is it possible/where should i put them?
.local? .icons? what would be the exact path?

---

### Post by sisco311 on 2009-09-30
~/.icons

---

### Post by Vaphell on 2009-10-01
what would be the exact path assuming default location of /usr/share/fast-user-switch-applet/icons/hicolor/22x22/status (there are different sizes+scalable)?

---

### Post by PrimoTurbo on 2009-10-02
I don't think you can't do it completely considering that many programs don't look for custom icons in home directory. You can only do it for gnome icon theme icons.

---

