---
title: "Installed Packages not from main and restricted"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-02-08
I would like to search for all the packages in my system NOT installed from "main" and "restricted" repositories...

Is there any quick command to do it from the command line? (or from aptitude..)

thanks!!

---

### Post by teaker1s on 2007-02-08
in terminal
[COLOR="Red"]sudo gedit /etc/apt/sources.list [/COLOR]



remove the [COLOR="Red"]#[/COLOR] to enable them 
[COLOR="SeaGreen"]save file as[/COLOR] and ok it to replace existing file on gedit
and reload/update and you should be able to install universe packages

---

