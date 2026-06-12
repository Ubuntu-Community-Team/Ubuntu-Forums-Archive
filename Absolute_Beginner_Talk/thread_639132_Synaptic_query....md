---
title: "Synaptic query..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by A$h X on 2007-12-12
Okay regarding the rather wonderful synaptic package manager, i have a question. In the status window on the left, what do the options "Installed (local or obsolete)" and "Not installed (residual config)" mean? Can i delete these packages without harming my system? And if they are not being used, then why haven't they been deleted already? Unless another app is depending on a shared library or something.

---

### Post by oeolycus on 2007-12-12
From my understanding Installed (Local / Obsolete) are packages you've installed yourself (via dpkg) and without Synaptic. Not Installed (Residual Config) are packages you've removed but which may still have configuration files on the computer (aha, residual config!) and may still be in the deb cache (for quick reinstallation).

Hope that helps. I ended up looking through the Ubuntu help and Synaptic How-To, and then all of Synaptic's website and several Debian manuals to try to find a quotation to point you to, but the easiest solution is usually the best, and a Google search of "synaptic residual config" yielded the answer I just gave you.

---

### Post by A$h X on 2007-12-12
Cheers bro, perhaps a tooltip popup could explain to new users when hovering over the options. something for the dev team to think about.

---

