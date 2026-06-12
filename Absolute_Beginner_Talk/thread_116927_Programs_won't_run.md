---
title: "Programs won't run"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Patient Samurai on 2006-01-13
Hi. I just started using Linux over the past week, and through the help of my friend I've finally got it running. Everything seems to work fine except many programs won't run. Over the process of installing, reformating and re-installing I've installed Breezy Badger about 7 times now. The very first time I clicked on update, and Linux happily updated everything itself while is was logged in as a non-root user. Ever since then, update won't run. Other things won't either: almost all "administration" or "configuration" type programs.  What can I do?

---

### Post by adwait on 2006-01-13
To run any program which requires root access, in the terminal type
```
sudo <program name>
```

Type your own user password when it asks for it.

---

### Post by Patient Samurai on 2006-01-14
Still nothing happens... :(

---

### Post by JimmyJazz on 2006-01-14
[QUOTE=Patient Samurai]Still nothing happens... :([/QUOTE]

is it finding 'sudo'? does it give you any output when you type that in terminal?
you might not have adminstrative user privileges.

---

### Post by Patient Samurai on 2006-01-14
It asks me for my password, then does nothing.

---

### Post by Patient Samurai on 2006-01-14
After searching through tons of forums I figured it out (kinda). I used su -s and it worked. But why doesn't sudo work, and why can't I open the programs without going into the terminal? Could it be that my user doesn't have the proper permissions, and if so, I do i fix that?

---

