---
title: "How can I remove these program?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Mykas0 on 2007-08-13
More often than not, when I try to remove an application via Synaptic I end up gettiing a message which states that it will also remove 'ubuntu-desktop'.

So, my question is... is it actually OK to remove such an application? I tried to remove, for example, 'Serpentine' and 'Gimp', as I don't really use them, and I can't.... In general, is it OK to remove applications that give me this sort of message, i.e. that they depend on 'ubuntu-desktop' (or something like that?)?

---

### Post by Steveway on 2007-08-13
Ubuntu-Desktop is just a Meta-package, you can remove it safely.

---

### Post by Mykas0 on 2007-08-13
OK, thanks!

---

### Post by Arthur Archnix on 2007-08-13
It's safe to remove, but if the time comes when you want to upgrade to Gutsy Gibbon, you won't be able to do a simple apt-get dist-upgrade. You may have to reinstall the ubuntu-desktop first, or just do   a clean install from cd.

---

