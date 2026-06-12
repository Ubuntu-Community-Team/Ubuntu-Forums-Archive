---
title: "PHP5/Apache2 problem"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-05-22
Hi

I am running Ubuntu 7.04. Until this morning i had a perfectly working Apache2 / PHP5 server configuration running on my machine but i managed to break it uninstalling KDE (Which was on my computer because i got bored of Gnome but i hated it). So i reinstalled it and now whenever i try to run a php script firefox tries to save it as a phtml file. I have reinstalled PHP and Apache multiple times so it must be a config problem , but i dont know where to start trying to fix it.

Bobbo

---

### Post by az on 2007-05-22
> **bobbocanfly said:**
> Hi

I am running Ubuntu 7.04. Until this morning i had a perfectly working Apache2 / PHP5 server configuration running on my machine but i managed to break it uninstalling KDE (Which was on my computer because i got bored of Gnome but i hated it). So i reinstalled it and now whenever i try to run a php script firefox tries to save it as a phtml file. I have reinstalled PHP and Apache multiple times so it must be a config problem , but i dont know where to start trying to fix it.

Bobbo

Installing or removing kde will not affect LAMP.  Unless you removed some of the lamp packages too, which should not be the default behaviour.

Is libapache2-mod-php5 still installed?

---

### Post by bobbocanfly on 2007-05-22
I was just given a big list of things by my friend to delete off of my computer to delete KDE, stupidly i didnt look through it properly and deleted some of my Apache files.

Yes libapache2-mod-php5 is on my computer.

---

