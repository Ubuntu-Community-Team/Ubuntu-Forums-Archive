---
title: "pls i need repositries"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2008-01-29
i need repositries for my ubuntu that will enable me with my school work and my computer skills am a student of electronics engineering and got skills in computer thanks

---

### Post by bodhi.zazen on 2008-01-29
what do you need ?

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by nnamdi on 2008-01-29
thanks for quick reply i just started usin linux and i want to use far more just a desktop user i want to go into high techy stuff actually prepare my self for the market( work force) will soon be rounding up with university

---

### Post by Luke771 on 2008-01-29
In a terminal, type:```

sudo gedit /etc/apt/sources.list
```

uncomment the all commented-out lines that begin in "deb"
save and close.

---

### Post by Joeb454 on 2008-01-29
While Luke771 is correct, the correct command for opening it is slightly different.

You should use ```
gksu gedit /etc/apt/sources.list
```

---

### Post by JoshuaRL on 2008-01-29
> **Joeb454 said:**
> While Luke771 is correct, the correct command for opening it is slightly different.

You should use ```
gksu gedit /etc/apt/sources.list
```

Yeah, I just learned that. (Thanks Glotz!)  It saves you from messing up your permissions.  It won't always make a difference, but use gksu whenever you need to use a graphical program with admin priviledges.  Always better safe than sorry.

---

