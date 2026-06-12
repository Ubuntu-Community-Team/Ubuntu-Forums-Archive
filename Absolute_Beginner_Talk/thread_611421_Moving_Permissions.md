---
title: "Moving Permissions"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-12
Hi, when i attempt to move a folder to my /usr/games folder, it says i do not have permissions.  How do i do this?

---

### Post by Atreus12 on 2007-11-12
/usr/games is owned by root

the files you own are under /home/your_user_name

if you want to move them, the easiest way is probably the terminal

```

sudo mv /path/to/files/to/be/moved /usr/games

```

sudo is short for "super user do", in essence temporarily enabling root access.

-Andrew

---

### Post by Partyboi2 on 2007-11-12
> **jordank said:**
> Hi, when i attempt to move a folder to my /usr/games folder, it says i do not have permissions.  How do i do this?

```
sudo mv <*file***> /**usr/games
```
To change permissions, I think its:
```
sudo chmod o+x <*file>*
```

---

### Post by jordank on 2007-11-13
thank you :)

---

### Post by CatKiller on 2007-11-13
Actually, I think the **easiest** way for us point-and-drool users is graphically. You can open a file browser window as *root* by running ```
gksudo nautilus
``` although you should obviously be careful about what you do with that - you only have permissions to your Home folder for a reason.

A useful tip I picked up on this forum is to change the profile of *root*'s nautilus windows to remind you not to use it all the time. The background of mine is a particularly hideous shade of pink, for example.

---

