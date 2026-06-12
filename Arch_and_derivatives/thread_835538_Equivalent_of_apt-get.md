---
title: "Equivalent of apt-get *"
date: 2008-06-20
forum: Arch and derivatives
---

### Post by gfg on 2008-06-20
Hello! Does anyone know if there is a pacman equivalent of "apt-get *"? What I am trying to do is install all packages with the name fortune-mod. I haven't found any command to do this with pacman. Is this possible, or do I have to install every package manually?

---

### Post by Barrucadu on 2008-06-20
You have to install them all manually, pacman doesn't support wildcards.
I suppose you could try to cobble together a script to search the database, use grep for the regex, and pass the matching packages to pacman, but it could waste more time than it would save.

---

### Post by kalpik on 2008-06-20
You can try yaourt! yaourt fortune-mod. It will show you all packages with fortune-mod and then you can just select all to install :)

---

### Post by gfg on 2008-06-21
> **kalpik said:**
> You can try yaourt! yaourt fortune-mod. It will show you all packages with fortune-mod and then you can just select all to install :)

Yes, I tried it. It's very usefull, and allowed me to select the packages I wanted easily by typing a number range. Thanks.

---

### Post by Patogen on 2008-06-21
pacman -S `pacman -Ss fortune-mod | grep fortune-mod | awk '{print $1}'`

Will install all packages named fortune-mod. There is probably a smarter way of doing this as well, but it works. Notice it's ticks `, not ' (except for the awk part).

---

### Post by handy on 2008-06-22
[***_tupac_***]("http://wiki.archlinux.org/index.php/TuPac") may make it quicker for you.

---

