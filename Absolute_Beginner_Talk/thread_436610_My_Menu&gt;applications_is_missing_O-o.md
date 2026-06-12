---
title: "My Menu&gt;applications is missing O-o"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Atow on 2007-05-08
ok i did a fresh install and i finally found a way to make my wireless card work through a netowrk manager i installed, and i double clicked it after install and everythign worked fine and it told me to activate it all i had to do was go to menu>applications>network manager. however menu>applications doesnt exist under my menu, and i dont know where on my hard drive i could find the network manager executable. help?

---

### Post by Ozeuss on 2007-05-08
I don't think i understand you. are you missing the whole "Applications" menu, or just the entry? is that the network manager that comes with ubuntu or another one?

---

### Post by Atow on 2007-05-08
> **Ozeuss said:**
> I don't think i understand you. are you missing the whole "Applications" menu, or just the entry? is that the network manager that comes with ubuntu or another one?

im missing the whole applications menu and its another one i found in the add/remove that i installed and made it work, not the normal menu>system>network feature

---

### Post by Ozeuss on 2007-05-08
first off, you can add a 'fresh' main menu by rightclicking the panel>add to panel> and add "Menu Bar"
second, you still haven't told us the name of the package you installed. you should be able to start it from the terminal.

---

### Post by Atow on 2007-05-08
> **Ozeuss said:**
> first off, you can add a 'fresh' main menu by rightclicking the panel>add to panel> and add "Menu Bar"
second, you still haven't told us the name of the package you installed. you should be able to start it from the terminal.

its the network management framework (gnome front end)
[www.gnome.org/projects/networkmanager](www.gnome.org/projects/networkmanager)

and i know i can add a menu bar but i cant find the application

---

### Post by Ozeuss on 2007-05-08
network manager comes by default in ubuntu...
that supposed to load by default. check if network-manager-gnome is installed, then check if network manager appears in your start up "sessions" window (under System>preferences)
and then you can log out and log back in, or restart networking by
```
sudo /etc/init.d/networking restart
```

---

### Post by Atow on 2007-05-08
> **Ozeuss said:**
> network manager comes by default in ubuntu...
that supposed to load by default. check if network-manager-gnome is installed, then check if network manager appears in your start up "sessions" window (under System>preferences)
and then you can log out and log back in, or restart networking by
```
sudo /etc/init.d/networking restart
```

yes its installed because i installed it earlier, and no its not in my start up sessions window and that command line u gave me does not exist.

---

