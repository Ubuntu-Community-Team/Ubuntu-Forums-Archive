---
title: "Recycke bin"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-24
How do i make i icon of the recycle bin on my desktop?

---

### Post by techno-mole on 2007-05-24
the way i do it is-

alt + f2 then type gconf-editor then click run
goto apps-- nautilus-- desktop
check the trash can visable box the hit enter
and the bin should be on the desktop
this is how i used to do it in edgy, dont know if its the same in fiesty

i just tried it and it still works

---

### Post by bashologist on 2007-05-24
Here's another method:

gconftool-2 -s /apps/nautilus/desktop/trash_icon_visible --type=bool true

---

### Post by blackened on 2007-05-24
I'm on a windows machine right now, so this may not be perfect, but should get you close.

ALT+F2 -> gconf-editor
In gconf go to Applications -> Nautilus -> Desktop
and select 'show trash on desktop' (or something similar, it's the last entry in the right-hand pane)

---

