---
title: "where is the Users and Groups menu item?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by alexroot on 2006-12-15
I read a guide somewhere about changing a user's home directory and it said i should go to:System, then Administration and then the Users and Groups menu item. And that menu item doesn't appear on my install. 

 can i install it without having to reinstall my system?

if not, what's the easiest way to change a user's home directory?

thanks

---

### Post by lance_klusener on 2006-12-15
What version of ubuntu are u using

---

### Post by cetheriel on 2007-08-11
I'm using feisty...
actually, just for a complete story, my ubuntu cd was kinda broken so i installed only the command line system, then aptitude ubuntu-desktop metapackage...
everything setup very well, system runinng alright. just that users and groups link missing.
what should i apt-get?

---

### Post by eapache on 2007-08-11
Right-click on the menu and say 'edit menu' then browse down to it and see if that option has a check-mark next to it. If not, add one.

---

### Post by cetheriel on 2007-08-11
> Right-click on the menu and say 'edit menu' then browse down to it and see if that option has a check-mark next to it. If not, add one.
there's not such option...

---

### Post by yorkie on 2007-08-11
Are you looking for the users and group menu or  the change home directory option

---

### Post by cetheriel on 2007-08-11
users and groups menu under system>admin

---

### Post by yorkie on 2007-08-11
/home/alf/Desktop/utils/wallpaper/Screenshot-Main Menu.png
this is result of right click on SYSTEM > EDIT MENUS does yours look like this
.

---

### Post by aysiu on 2007-08-11
Paste these commands into the terminal: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
gksudo users-admin
```

---

### Post by cetheriel on 2007-08-12
thank you aysiu. i actually broke the ubuntu-desktop package, since i didn't want evolution, so what i did was try to run users-admin. gksudoing it returned nothing, but simply running it returned a message:
```
El programa 'users-admin' puede ser encontrado en los siguientes paquetes:
 * gnome-system-tools
 * xubuntu-system-tools
Pruebe: sudo apt-get install <paquete seleccionado>
bash: users-admin: orden no encontrada
```
then i just typed
```
apt-get install gnome-system-tools
```
and gksudo users-admin worked. i wanted to restart X and check the menu, but it is there already. thank you very much.

---

### Post by cetheriel on 2007-08-12
found out exactly what i did not install. since it was supposed to install command line only, it did not install gnome-desktop-environment. found out by searching packages that depended on gnome-system-tools. then it came up (with several others, but this one makes sense).
installing it right now (but i&#314;l have to re-un-install evolution...)

---

