---
title: "Kubuntu read only mode"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-16
i just finnished installing kubuntu and im still showing my gnome interface i dont know if things are supposed to look different right away or not.  oh well i open the adept manager and i get this message.

"You will not be able to change your system settings in any way (install, remove or upgrade software), because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions"

anyone know why or how this happened, and more importantly how to fix it?  

another question is if i work in the adept manager and install certain KDE things how will this message affect things?

thanks for you time.

---

### Post by Capricori on 2007-10-16
It looks the same because Gnome is still the default desktop environment. On the login screen, there should be a menu button somewhere, which will allow you to change session type. Change it to KDE, and then login normally to see the changes :)

Secondly, that message means that you are about to play with things that can cause problems if you don't do them properly, so it wants you to run the program as root (the all powerful superuser). A box should appear when you try to open Adept that will allow you to enter the root password. (NB: the root password should be the same as your login, unless you change it).
If you don't get the pop-up box, try opening a terminal and typing "gksudo adept_manager" if you're using Gnome, or "kdesu adept_manager" if you're using KDE.

---

### Post by linux-loser on 2007-10-16
cool it works now, thanks for your help.

---

