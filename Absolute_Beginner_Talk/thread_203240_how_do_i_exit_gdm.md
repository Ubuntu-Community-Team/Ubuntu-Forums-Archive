---
title: "how do i exit gdm?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-06-24
without uninstalling it or tying it to a tree?

---

### Post by adwait on 2006-06-24
Press Shift + Alt + F1. The use
```
sudo /etc/init.d/gdm stop
```

---

### Post by fuscia on 2006-06-24
[QUOTE=adwait]Press Shift + Alt + F1. [/QUOTE]

nothing happens when i do this.

---

### Post by Sye d'Burns on 2006-06-24
Try ctl+alt+f2

---

### Post by fuscia on 2006-06-24
[QUOTE=Sye d'Burns]Try ctl+alt+f2[/QUOTE]

that got me a blank screen, but alt+f6 didn't bring up the console. i have a laptop with dapper installed.

---

### Post by Sye d'Burns on 2006-06-24
hmmm, really if you type **sudo /etc/init.d/gdm stop** in a terminal, it should throw you into a console login. I don't typically CTL+ALT+F# to stop gdm. Give it a go from a terminal.

---

### Post by fuscia on 2006-06-24
[QUOTE=Sye d'Burns]hmmm, really if you type **sudo /etc/init.d/gdm stop** in a terminal, it should throw you into a console login. I don't typically CTL+ALT+F# to stop gdm. Give it a go from a terminal.[/QUOTE]

tried it and got the blank screen again. when i uninstall gdm, i can get the console fine.

---

### Post by Sye d'Burns on 2006-06-25
[QUOTE=fuscia]that got me a blank screen, but alt+f6 didn't bring up the console. i have a laptop with dapper installed.[/QUOTE]

Ooh, ooh, laptop, missed that... Try CTL+ALT+F6

---

### Post by fuscia on 2006-06-25
[QUOTE=Sye d'Burns]Ooh, ooh, laptop, missed that... Try CTL+ALT+F6[/QUOTE]

still getting a blank screen. is bringing up the console different on a laptop, as well? this thing is new.

---

