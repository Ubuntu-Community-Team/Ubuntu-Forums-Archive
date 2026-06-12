---
title: "Administrative Permissions"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by LJarvis on 2007-05-18
I'm new to Ubuntu and whenever i try to copy files to certain folders i will get this error:

You do not have permissions to write to this folder.

Is there any way that i can change my administrative privileges to allow me to copy files anywhere i need to?

---

### Post by finer recliner on 2007-05-18
welcome to linux. read here for more information:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Foxmike on 2007-05-18
You can open a file manager by typing in a terminal:
```
gksudo nautilus
```
if you are using GNOME or
```
kdesu konqueror
```
if you are under KDE.
 
A pop-up window will appear asking you for your password. Then the proper file-manager will open.
 
Althought, I would take a great care of what I do then because those commands will allow you to copy/remove any file anywhere on your system using the file-manager and it could break your system. You should do this only (**_and only if_**) you know exacty what you are doing. My suggestion is: if it is the case, open the file-manager that way, do what you have to do and close it right away.
 
Hope it helps!:)
 
Regards,
 
-FM

---

### Post by Foxmike on 2007-05-18
> **finer recliner said:**
> welcome to linux. read here for more information:
 
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
 
Damn fast typer!:)
 
Regards,
 
-FM

---

### Post by LJarvis on 2007-05-18
> **Foxmike said:**
> You can open a file manager by typing in a terminal:
```
gksudo nautilus
```
if you are using GNOME or
```
kdesu konqueror
```
if you are under KDE.
 
A pop-up window will appear asking you for your password. Then the proper file-manager will open.
 
Althought, I would take a great care of what I do then because those commands will allow you to copy/remove any file anywhere on your system using the file-manager and it could break your system. You should do this only (**_and only if_**) you know exacty what you are doing. My suggestion is: if it is the case, open the file-manager that way, do what you have to do and close it right away.
 
Hope it helps!:)
 
Regards,
 
-FM

Thanks so much im never going to forget that command.

---

### Post by ugm6hr on 2007-05-18
I use Xubuntu7.04, and have found that it's helpful to have an icon in the top taskbar which launches Thunar (Xubuntu file manager) as root user, but starting at my user's directory (i.e. My Documents equivalent).

I just edited the pre-existing icon: changed the "command" from "thunar" to "gksudo thunar"

So now I have a desktop icon for standard files transfers and a taskbar entry (as root) for anything else.  Easy...

---

