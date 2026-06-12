---
title: "Problem with Xorg | translucency and shadows -- PLEASE help"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by thedoors on 2006-11-19
Ok i have this problem:
I right clicked the toolbar > configure panel > and selected translurency etc.
Now every time i boot up KDE it gives me those 2 errors:

Composite manager crashed twice within a minute , and it won't be used for this session.
--------
You must use XOrg ? 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

How do i turn it off?
I tried from Kcontrol but i can't find it... Can anyone tell me exactly where it is?
thx,
thedoors

---

### Post by slimdog360 on 2006-11-19
I cant remember exactly where it is but I do know it is in kcontrol. Just keep looking.

---

### Post by LLRNR on 2006-11-19
Yup I think I found it: Look in KControl -> Desktop -> Window Behavior -> Translucency tab sheet -> de-check the box labelled "Use translucency / Shadows".

---

