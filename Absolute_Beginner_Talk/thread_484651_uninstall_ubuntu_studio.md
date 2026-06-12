---
title: "uninstall ubuntu studio"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by mexicancupcak3 on 2007-06-26
i installed ubuntustudio from the commands for the terminal. and ive decided i dont care for it . how do i go about going back to my noraml ubuntu?

---

### Post by cogadh on 2007-06-26
Try this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by deadgobby on 2007-06-26
DO NOT DO THAT! From the second post, it will mess things up. Like remove the desktop. Just go into Synaptic and do it.
 PS you can just live with all the programs and play them at your own will. Now just where is the manual for third party software?

---

### Post by cogadh on 2007-06-26
> **deadgobby said:**
> DO NOT DO THAT! From the second post, it will mess things up. Like remove the desktop. Just go into Synaptic and do it.
 PS you can just live with all the programs and play them at your own will. Now just where is the manual for third party software?

Apt-get is the same as Synaptic, it is just a terminal application instead of a GUI. The command I offered will **not** uninstall anything, it just installs the default Ubuntu desktop and all its dependencies, which is exactly what mexicancupcak3 asked for. The only way apt-get would uninstall the desktop is if you use the "remove" option instead of the "install" option.

I have used this same command to turn both Kubuntu and Xubuntu into Ubuntu, there is absolutely no reason it shouldn't work with Ubuntu Studio.

---

