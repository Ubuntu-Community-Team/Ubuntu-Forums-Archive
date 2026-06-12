---
title: "recovery help"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by killaray on 2006-12-19
i need help recovering my GNome interface... somehow i uninstalled it and cant access ubuntu in a graphical interface.. im using my live cd now cause i thought there would be some way to just copy over the files i needed but i cant get my primary HD to mount. ive tried installing gnome threw the terminal but it never actually goes threw. anyone know how i can reinstall GNome?

---

### Post by bulldog on 2006-12-19
Boot into the console or use the recovery mode and type after login```
sudo aptitude install ubuntu-desktop
```
This should repair your GUI with a little luck of course :D

---

### Post by killaray on 2006-12-19
thats wut i was trying to due..i got it to work cause it kept sayin to do dpkg -a or something like that, anywho im back up and running and thank u for that but now i have a whole bunch of debian apps in my applications menu.. how can i remove them??

---

### Post by killaray on 2006-12-20
noone knows how to remove them?

---

### Post by aysiu on 2006-12-20
Right-click on the Applications button and select **Edit menus** and then uncheck whatever boxes you don't want to see.

---

### Post by killaray on 2006-12-21
so u cant actually remove the programs?

---

### Post by Axis on 2006-12-21
Unless I am mistaken (which is very well possible I am new to all of this) yes you can uninstall just about anything. After unchecking the items you click apply and it makes sure you understand the changes. After you select yes it makes the changes, in your case un-installing the unwanted programs.

---

