---
title: "gtk-theme-switch2 problems"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-09-08
it will allow me to pick some gtk themes, but not all of them. gtk-chtheme works for all, but won't recongnize .gtkrc-2.0.mine.

---

### Post by diatribe on 2007-09-08
when you say pick some does it only list some of them, or will allow you to actually select some of them?

---

### Post by fuscia on 2007-09-08
> **diatribe said:**
> when you say pick some does it only list some of them, or will allow you to actually select some of them?

it lists all the themes i have, but when i select some of them, it just picks some ugly default looking thing.

---

### Post by diatribe on 2007-09-08
I have had this same issue, I thought it was a gutsy thing.  Reinstalling the theme engines (aurora in my case) solved it for me though.

---

### Post by fuscia on 2007-09-08
fixed it for gtk-chtheme. in my .gtkrc-2.0 file, the include was pointing to .gtkrc.mine, not .gtkrc-2.0.mine. i just renamed it to .gtkrc.mine and all is fine with gtk-chtheme. to hell with gtk-theme-switch2! thanks for the response.

---

### Post by diatribe on 2007-09-08
haha well as long as it works that it whats important :D

---

