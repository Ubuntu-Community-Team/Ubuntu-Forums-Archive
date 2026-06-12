---
title: "installed packages?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by seanm on 2006-07-04
hi there - does anyone know what the command i type to find out what packages are install on my machine - also what is packages are needed to enable a gui interface using server 6.0.6 lts?

many thanks

Seanm:confused:

---

### Post by ProjectGod on 2006-07-04
try 
[B]sudo aptitude
[/B]
put in your password when prompted... in aptitude you can use keyboard arrows and enter etc to locate "installed packages".

---

### Post by seanm on 2006-07-04
thanks 

Seanm:p

---

### Post by aysiu on 2006-07-04
Won't this work? ```
dpkg -l
```

---

### Post by Qrk on 2006-07-04
[QUOTE=seanm]hi there - does anyone know what the command i type to find out what packages are install on my machine - also what is packages are needed to enable a gui interface using server 6.0.6 lts?

many thanks

Seanm:confused:[/QUOTE]

To get a desktop installation from the sever, you only need to install ubuntu-desktop (for gnome), kubuntu-desktop (for KDE), or xubuntu-desktop (for xfce)

```
sudo apt-get install ubuntu-desktop
```

these will install all the packages you need to get a GUI, plus some more.

---

