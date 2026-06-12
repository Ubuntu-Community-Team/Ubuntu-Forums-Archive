---
title: "[SOLVED] Still getting used to pacman. Question."
date: 2008-03-13
forum: Arch and derivatives
---

### Post by Pogeymanz on 2008-03-13
How can I get pacman to remove unneeded dependencies that are left behind. So far, for uninstalling something I've just been using "pacman -R package" instead of "pacman -Rs", which I believe removes the dependencies as well.

I want to clean up the dependencies I've left by not including that s.

---

### Post by Rumor on 2008-03-13
**pacman -Qdt** will give you a list of orphaned packages. You can then remove them individually.

---

### Post by Pogeymanz on 2008-03-13
Cool!

---

### Post by PurposeOfReason on 2008-03-14
Just a note to be careful what you remove from that list. Things such as autoconf and make will appear on that list and I'm sure you'll want those.

---

### Post by K.Mandla on 2008-03-16
I usually rip things out with *yaourt -Rcsn pkgname*, but that will occasionally try to pull out unrelated software, if it shares a dependency.

---

