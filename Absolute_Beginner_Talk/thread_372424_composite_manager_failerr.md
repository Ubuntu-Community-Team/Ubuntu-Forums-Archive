---
title: "composite manager failerr ?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by graha on 2007-02-28
what is that ? 'composite manager failer'  everytime i log in this message comes out 
one of them us
**Composite extension not found**
You must use Xorg _>_ 6.8 for translucency and shadows to work.
Additionaly, you need to add a new section to your xconfid file:
*section* "*externesions*"
_option "Composite" "enable"_
End section

and the other on is
the composite manger crashed twice within a minute and is therefore disabled for this session.

i have no idea what all this mean

---

### Post by Bachstelze on 2007-02-28
If you want to use a compositing WM, you obviously need to enable compositing in your xorg.conf. Add the three suggested lines at the end of it.

---

