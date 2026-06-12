---
title: "problem with icewm and metacity"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2006-10-09
hi all .
i dont know why but so hard to understand . when my ubuntu boot , it use icewm window manager (even my default session is gnome) , so i must change window manager to metacity everytime ubuntu boot . and it also the reason that it make the sound mute .
i also try to uninstall icewm from snaptic but after that it make metacity lose the border (i go to theme -> detail and just see controls and icons)
thanx for ur helps . i really want to fix this asap . it disturb me everyboot ](*,)

---

### Post by ghostshadow189 on 2006-10-09
hi all , i found the way to fix :D
change this in ~/.gnome2/session -> 0,RestartCommand=metacity  (it's 0,RestartCommand=icewm before)

---

