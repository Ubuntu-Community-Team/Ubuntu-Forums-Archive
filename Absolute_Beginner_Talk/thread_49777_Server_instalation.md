---
title: "Server instalation"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by ufa on 2005-07-17
I did a server installation, because my system (/) HD is only 1.6 ( i have the /home in other HD). But i want to install the graphic interface (Gnome) but the apt-get did not regognized the packet gnome or gnome-desktop. What is the package that i must install  to have graphical interface in a server installation? I dont want to make a full installation, nether the server installation, i want something between them that fit in my 1.6 GB HD.
Regards
Ufa

---

### Post by Kyral on 2005-07-17
I'd try something that depends on the gnome libs. Try something like gnome-bin. But you can also try XFCE, lightwieght and doesn't take up much space.

But yah....this could all be solved through having meta-packages for GNOME and KDE to install those seperatly....

---

### Post by ufa on 2005-07-17
[QUOTE=Kyral]I'd try something that depends on the gnome libs. Try something like gnome-bin. But you can also try XFCE, lightwieght and doesn't take up much space.
[/QUOTE]

I tried to install gaim, gnome-games, it installed, but gnome didnt install enough to run.
:(

---

### Post by Kyral on 2005-07-17
If you really have your heart set on GNOME, then keep trying. Honestly I don't know what libs and whatnot make up GNOME. But if you can live with something else, try XFCE. Its very good :D

---

### Post by ufa on 2005-07-17
[QUOTE=Kyral] But if you can live with something else, try XFCE. Its very good :D[/QUOTE]

Thx Kyral, i will try that!!
to install it just apt-get XFCE??

---

### Post by Kyral on 2005-07-17
sudo apt-get install xfce4 (there is an xfce package, but I dunno what the difference is)

---

### Post by UbuWu on 2005-07-17
For a basic gnome desktop:
sudo apt-get install gnome-desktop-environment

---

### Post by UbuWu on 2005-07-17
And if you want a little more, you have to edit your sources.list to enable the universe repository, and then you can do a apt-get install gnome, which will give you the same gnome desktop + some extra's like totem, rhythmbox, evolution and some more.

---

### Post by ufa on 2005-07-18
[QUOTE=UbuWu]And if you want a little more, you have to edit your sources.list to enable the universe repository, and then you can do a apt-get install gnome, which will give you the same gnome desktop + some extra's like totem, rhythmbox, evolution and some more.[/QUOTE]

Sweet..I will try that, but i cannot reach the 1.6 GB limit, if it doesnt work, i will be with just gnome-desktop-environment or XFCE

---

