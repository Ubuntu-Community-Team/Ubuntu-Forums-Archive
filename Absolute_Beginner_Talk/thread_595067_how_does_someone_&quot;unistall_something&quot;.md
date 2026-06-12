---
title: "how does someone &quot;unistall something&quot;?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-10-28
Greeting all,
I recently installed moblock onto my system, and now I cannot access any pages on my system.  I saw on another forum (peerguardian linus alternative) about doing a white list, but I tried that with no success.  Is there anyway I can remove this program (ie unistall)?

---

### Post by krisfrajer on 2007-10-28
Did you try the add/remove software in the "application menu"?
or maybe using synaptic in the "system menu"?

That would be the first places I would check to uninstall programs. I hope this helps :)

---

### Post by mikewhatever on 2007-10-28
You can remove them, but fist tell us how they were installed, in other words, from synaptic, from a downloaded deb file, or from a tar ball.

---

### Post by Crafty Kisses on 2007-10-28
Usually the command is:
```
sudo apt-get remove package name
```

---

### Post by mangurt on 2007-10-28
Thanks!  The synpatic package manager did the trick.  Now I can surf around on my computer again :)

---

