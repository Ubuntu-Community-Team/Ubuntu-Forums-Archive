---
title: "turn off xserver"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by koconnor100 on 2007-04-30
How do I turn off the graphics server so I can mess with the video drivers ?

---

### Post by Nythain on 2007-04-30
in gnome, log out, start a console session, log into it and type sudo /etc/init.d/gdm stop
replace gdm with kdm for kde

---

### Post by koconnor100 on 2007-04-30
almost there ... 

I think my real question was ...how do you log out of gnome so you're at the Linux prompt ?

---

### Post by Nythain on 2007-04-30
not sure of the correct way since i run kde... ctrl alt backspace will get you there though, then from the login screen just select like console login or whatever its called... should do the trick...

---

### Post by bobplano on 2007-04-30
you can use a terminal just use ctrl+alt+f1-6 to get to a terminal and then ctrl+alt+f7 to get back to the GUI

---

### Post by koconnor100 on 2007-04-30
> **bobplano said:**
> you can use a terminal just use ctrl+alt+f1-6 to get to a terminal and then ctrl+alt+f7 to get back to the GUI

Tried a termina (from the menu) it crashed everything ...

well....ctl alt f1 ...why not ....

nope ! 

Well...yes , it scucessfully put me in a linux prompt so I could run envy -t 

no , running envy -t didn't solve my problems. I'm still stuck in 640x480 graphics mode

---

