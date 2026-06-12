---
title: "How to force gnome to use icons with fixed sizes?"
date: 2007-12-25
forum: Art &amp; Design
---

### Post by Joe_Bishop on 2007-12-25
Hi!
I used nimbus icon theme, but in the menues (Applications, Places, Systems) gnome uses icons different from 24x24, although their size is 24x24. Icons 24x24 is present in the nimbus icon theme. How can I force gnome to use them?

---

### Post by webdesigncompany on 2008-01-03
hi i have the same question too

---

### Post by NilsE on 2008-01-03
Delete the other sizes (just leave 24x24 and Scalable) from the folder in 

/urs/share/icons

and edit the 

index.theme 

in same folder and remove the entries for the deleted folders.

---

