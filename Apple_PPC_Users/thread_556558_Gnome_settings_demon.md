---
title: "Gnome settings demon"
date: 2007-09-21
forum: Apple PPC Users
---

### Post by Stuart47 on 2007-09-21
sorry couldn't see this anywhere else 
 on loading of the log on screen every thing is fine for a few seconds then it goes slow and jumpy i log-on and it stalls on the brown screen for ages and then a window pop-up saying that the gnome-settings-demon was refused by the system and failed to load after a time the desktop loads and you can use all the apps but it is still horribly slow i went in to the system monitor and its siting at 97% there are no other apps running or using the cpu and i try to update the software but the gui updater dosnt down load anything just hangs on the first down load after using sudo apt-get update/upgrade it gets every thing but the Gnome updates

iMac G5 revA i think
geforce fx 5200
G5 PPC 1.8GHz
1.2GB RAM

---

### Post by stmiller on 2007-09-21
Hey try these things:
```

sudo apt-get remove mouseemu

```

And also go to the Gnome Sound preferences and uncheck the 'ESD' checkbox.

---

