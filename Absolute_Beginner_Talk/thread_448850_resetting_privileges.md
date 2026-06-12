---
title: "resetting privileges?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by danh86 on 2007-05-19
I've got one main user account on my Ubuntu install, which I believe differs to a 'root' user, but still has high admin rights. I've somehow managed to disallow myself certain rights, such as being able to add/remove programs and create other users; the 'users' button on the system menu has dissapeared, and so I can't log into my normal account and change the privileges etc. back to how they were. 

I've tried searching the forums but I can't seem to find any easy fixes. Does anyone know how I can reset my main account back to it's original settings?

Thanks in advance,
Dan

---

### Post by bodhi.zazen on 2007-05-19
Depends on what you did to disallow your self.

You should have admin rights with the first user via sudo.

If not, add your user to the admin group.

---

### Post by danh86 on 2007-05-19
Is there an easy way of adding my first (and only) user account back to the admin group? I´ve never used command line; I managed to screwup the user settings by just playing within the GUI, but now, the ´users and groups' menu does not appear on the system menu.

---

### Post by Bachstelze on 2007-05-19
First, make sure it's *really* not in it.

```
cat /etc/group | grep admin
```

---

