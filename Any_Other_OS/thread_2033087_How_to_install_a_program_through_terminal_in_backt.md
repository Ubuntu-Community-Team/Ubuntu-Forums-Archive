---
title: "How to install a program through terminal in backtrack linux?"
date: 2012-07-25
forum: Any Other OS
---

### Post by mitsos1996 on 2012-07-25
I'm a begginer and i learned that u can install programms using a command in terminal? What is this command?
Furthermore, how can look for a program in terminal ... i read is something like apt-cache search <software> but it doesn't work?

---

### Post by Cheesemill on 2012-07-25
To install a program:
```
apt-get install <program>
```

To search for a program:
```
apt-cache search <field>
```

Before doing either of these make sure your package list is up to date by doing:
```
apt-get update
```

---

### Post by oldos2er on 2012-07-25
Moved to Other OS/Distro Talk.

---

### Post by Mr.Plex on 2012-07-27
If you burned it to a CD just forget about installing any other programs. It won't work. USB boot is a different story. Best of Luck!

[img]http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif[/img]

---

### Post by Cheesemill on 2012-07-27
> **Mr.Plex said:**
> If you burned it to a CD just forget about installing any other programs. It won't work. USB boot is a different story. Best of Luck!

:popcorn:
You can install whatever programs you want when using a Live CD, they just don't survive a reboot.

---

