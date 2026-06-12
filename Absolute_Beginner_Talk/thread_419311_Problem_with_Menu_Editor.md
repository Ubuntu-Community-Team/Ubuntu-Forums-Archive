---
title: "Problem with Menu Editor"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by loopeando on 2007-04-22
I've made a clean install of Ubuntu Feisty and I've one strange problem which I haven't had with Dapper or Edgy.

When I try to edit an item in the Applications menu, for example: when I try to edit the name of the item "Navegador web Firefox" (Yes, It's spanish) to "Firefox" the change won't apply. This happens with gThumb, f-spot, Rhythmbox or any other application.

Anyone know how to solve this?

Thx

---

### Post by Bias on 2007-04-23
Complete guess this. Maybe it needs to be running as root to have permissions to save. Not seen it on this particular app but have in others, find out what the app is called and then in termina try

sudo <app name>

Like I said it's just a guess.

---

### Post by loopeando on 2007-04-23
I've tried to enter to the menu editor, alacarte, in the terminal logged as a root and i get this:
[INDENT]
root@loop-laptop:/home/loop# alacarte
(alacarte:7027): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/INDENT]

And when I try to edit an item this:
[INDENT]
(gnome-desktop-item-edit:7035): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/INDENT]

---

