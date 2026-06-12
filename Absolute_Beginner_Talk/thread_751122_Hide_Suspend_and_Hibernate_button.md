---
title: "Hide Suspend and Hibernate button"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-10
When I press shut down, a box shows and tells me what to do.. 

how do I delete/hide the suspend and hibernate buttons?

Thanks,
Tom

---

### Post by nge on 2008-04-10
Go to Power Management in System then disable both.

cheers!

---

### Post by Tom--d on 2008-04-10
There is option to disable it.

---

### Post by stickx911 on 2008-04-18
I do not have that option in power management, but would like to disable both as well.

---

### Post by Tom--d on 2008-04-18
I know the option is in Xfce but not in Gnome. :(

---

### Post by sdennie on 2008-04-18
From a terminal:

```

gconftool-2 --type bool --set /apps/gnome-power-manager/general/can_hibernate false
gconftool-2 --type bool --set /apps/gnome-power-manager/general/can_suspend false

```

---

