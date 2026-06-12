---
title: "Starting linux without X...how?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-04-12
Whats the most graceful way to change Ubuntu so it does not boot into X during startup?

---

### Post by aysiu on 2006-04-12
Press Control-Alt-F1 and type ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo reboot
```

---

### Post by esteban2x on 2006-04-12
Ok then if you boot to the command line and want to start X Gnome, what command would you use?

---

### Post by aysiu on 2006-04-12
[QUOTE=esteban2x]Ok then if you boot to the command line and want to start X Gnome, what command would you use?[/QUOTE] ```
sudo /etc/init.d/gdm restart
```

---

### Post by dermotti on 2006-04-12
[QUOTE=aysiu]Press Control-Alt-F1 and type ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo reboot
```[/QUOTE]


That just stops GDM. After a reboot GDM is started again.... I dont want GDM automatically coming up ater a reboot.

---

### Post by aysiu on 2006-04-12
[QUOTE=dermotti]That just stops GDM. After a reboot GDM is started again.... I dont want GDM automatically coming up ater a reboot.[/QUOTE] There's probably an easier way to do this, but you can try installing *bum* and then disabling the GDM service.

---

### Post by dermotti on 2006-04-12
Ahh nifty program. This should work. Thanks.

---

### Post by trent dillman on 2006-04-12
Or sysv-rc-conf...

---

### Post by steve.horsley on 2006-04-12
bum is the easiest way to disable the gdm service. 

It's there in System->Admnistration->Services too, but if you try and stop it there, it kills X and therefore itself before saving the config so you can't disable it this way.

To restart X there are two ways. 
1) Log in and use **sudo /etc/init.d/gdm start** which will start the normal GUI login screen, or
2) log in and use the command **startx** which bypasses the graphical login, and will drip you back to a console when you choose logout.

---

