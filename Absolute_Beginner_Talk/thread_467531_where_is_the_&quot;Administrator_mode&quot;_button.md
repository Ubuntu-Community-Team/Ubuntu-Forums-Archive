---
title: "where is the &quot;Administrator mode&quot; button!! [Resolved]"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-06-07
Guys check the screen shot attached. I installed KDM recently on mykubuntu7 machine. In the "Appearance -System Settings" tab it says "Change at this section requires root access. Click the administrator mode button to allow modifications"!!! but where is the button???????????

---

### Post by Clay_Banger on 2007-06-07
there is a bug there, that stops the button from showing up. the alternative is to do this:
```
kdesu kcontrol
```
and change the kdm theme in that.

---

### Post by badguyanil on 2007-06-07
Thanks a ton!!!

---

### Post by Nekiruhs on 2007-06-07
no, its just ```
kcontrol
``` there is an administrator button inside. Otherwise it changes the settings for root and not your user.

---

### Post by Clay_Banger on 2007-06-07
> **Nekiruhs said:**
> no, its just ```
kcontrol
``` there is an administrator button inside. Otherwise it changes the settings for root and not your user.
its changing the kdm theme, no one is logged on. so i think it doesnt really matter. but kdesu kcontrol was the way i fixed mine.

---

