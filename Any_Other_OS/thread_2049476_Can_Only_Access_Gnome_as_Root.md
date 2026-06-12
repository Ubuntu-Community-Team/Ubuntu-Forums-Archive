---
title: "Can Only Access Gnome as Root"
date: 2012-08-28
forum: Any Other OS
---

### Post by mamamia88 on 2012-08-28
I just did an install of Arch with gnome and the only problem I have right now is that I can't access gnome as a regular user.    I can login into a created regular user account in the command prompt when arch starts but startx command only lauches the basic x.    i edited the xinitrc  file like they said and startx only gnome-shell when i'm logged in as root.  obviously i don't want this.  also i tried gdm but that won't let me login at all even though the usernames and passwords are the same.

---

### Post by wojox on 2012-08-28
> **mamamia88 said:**
>   i edited the xinitrc  file like they said and startx only gnome-shell when i'm logged in as root.

.xinitrc is in your user folder and not root's correct?

---

### Post by mamamia88 on 2012-08-28
> **wojox said:**
> .xinitrc is in your user folder and not root's correct?

pretty sure i followed the guide to the tea.   can't find the file in nautilus though.

---

### Post by mamamia88 on 2012-08-28
fixed it by moving the file.  somehow it ended up in root instead of home.

---

