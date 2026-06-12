---
title: "How to install gtk stuff?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-02-23
This may sound dumb, but how do you install a gtk engine?

---

### Post by yabbadabbadont on 2007-02-24
Is it in the repositories or is it one you need to build from source?

If it is in the repos, "sudo aptitude search gtk2-engines", then "sudo aptitude install gtk2-engines-XXXX" when you find one you want.  Just substitute "gtk-" for "gtk2-" to install gtk1 theme engines (if needed).

If you need to build it from source, you will probably need to install build-essential, xorg-dev, and various gtk*-dev packages just so that you can compile it.

---

### Post by yasenov on 2007-02-25
i wonder the same thing ,i knew how to install them,but can u please explain how to change them after being installed.

---

