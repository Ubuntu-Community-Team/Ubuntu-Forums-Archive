---
title: "need help switching kde to gnome and other stuff im a n00b!!!"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by jay1097 on 2007-03-06
hey
im running amd64 ubuntu 6.10 on my brand new laptop, dualbotted with vista. i have a few problems:
first off when i installed kde, i set kde as default on accident, i want to switch it back top gnome but i have no idea what to do, i have searched for help but havent had any luck. i tried to fix the setting in the /etc/X11/default-display-manager, but it doesnt work for me, i get a warning saying a i dont have the permission to do this, which is wierd because i am the only user on my PC.

also when i log on to gnome desktop i lost my shutdown icon in the GUI shutdown menu, i tried fixing this in the login menu options but i cant open the login menu options for some wierd reason. i kind-of feel that to fix this i need to set gdm back to default, but i dont really know.

anyway im really desperate for help, ive already tried looking for help on my own because i like to figure things out by myself but im completly stuck on what apperes to be, easy to fix problems! so before i just re-install everythning i decided to try the ubuntu forums for some help.

---

### Post by Obor on 2007-03-06
When you logging in you can go to: options - sessions and choose Gnome. Once you click ok it will ask you if you want it as default from now on (if its not a default already)
That should do.

In case you still want to edit /etc/X11/default-display-manager you can do so by going to Terminal and type
```
gksudo gedit /etc/X11/default-display-manager
```
the file should say something like
/usr/sbin/gdm

gksudo is graphical sudo which gives you "admin" rights. To learn about root privileges read this [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by jay1097 on 2007-03-06
Thanks the "gksudo gedit /etc/X11/default-display-manager worked perfectly" and i really apperciate the rootsudo link!! and the restart/shutdown icons are back on the powerdown menu! thank you again, just made my day.:)

---

