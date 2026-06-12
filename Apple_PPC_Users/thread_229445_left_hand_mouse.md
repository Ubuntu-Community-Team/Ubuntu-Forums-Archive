---
title: "left hand mouse"
date: 2006-08-04
forum: Apple PPC Users
---

### Post by blatny on 2006-08-04
pls help,  I have accidentally checked the box for lefthanded mouse on my PowerBook G4 and am now somehow really lefthanded. The mouse doesnt work and I cannot get back to change the setting back.

thanx, Radek

---

### Post by moma on 2006-08-04
You can switch (re-arrange) the mouse buttons with xmodmap command.

List available mouse buttons
$ xmodmap -pp

Swicth 'em for left handed person (the number of buttons will vary from mouse 2 mouse)
$ xmodmap -e 'pointer = 3 2 1 4 5'

Normalize
$ xmodmap -e 'pointer = 1 2 3 4 5'

---

