---
title: "User Login script."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by arron on 2008-01-26
How to i get a script or command to run when a user logs into Ubuntu (as that user)?  I tried .bash_login but that doesnt do the trick.

---

### Post by nemilar on 2008-01-26
```
~/.bash_profile
```

is the file executed for login shells.  For non-login shells, it's .bashrc.

This information can be found in the bash manual, by running

```
man bash
```

It's all the way at the bottom, under "FILES"

---

### Post by erginemr on 2008-01-26
And if you want to do it graphically, there is a tool called "Sessions" under Main Menu -> Preferences, from where you can adjust programs which you want to run at session start.

---

