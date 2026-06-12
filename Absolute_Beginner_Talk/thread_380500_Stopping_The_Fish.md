---
title: "Stopping The Fish"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by milad on 2007-03-09
Does anybody know how i can stop this "fish" ????

press Alt+F2 and enter "free the fish"   (without the quotations)

---

### Post by johnl on 2007-03-09
I didn't know about that -- it's pretty cool :) 

Anyway, I it looks like clicking on the fish will cause it to swim off the screen and not reappear.

---

### Post by milad on 2007-03-09
yeah it's cool, but i guess it doesn't like me that mushc. it scapes when i try to touch it with my mouse. :D

I could'nt find it in list of current processes.

---

### Post by johnl on 2007-03-09
Haha, now it keeps coming back.  I'm stuck with it too.

I tried using "xkill" and clicking on it, but that didn't work.  I dont see it in `ps aux` either.

I bet logging out and logging back in would fix it; if that doesn't restarting the X server (control+alt+backspace) might.


Edit:  It looks like it's part of gnome-panel.

Type "killall gnome-panel" to restart your panels and kill the pesky fish :)

---

### Post by milad on 2007-03-09
It worked.
anyway, it was fun.

Thanks man

---

### Post by Ek0nomik on 2007-03-09
All you have to do is edit the panel and remove it.

---

### Post by honns on 2007-03-10
ok so i had the fish, then i typed 'killall gnome-panel', the Power management icon suddenly became its own window.  now when i restart, the power managament icon is no longer at the top and i want it back :(.  If anyone has any idea how to get it back it would be really appreciated

---

### Post by Patrick K on 2007-03-10
I bet everyone who has looked at this thread has tried to Free the Fish. I'm watching him right now.

---

### Post by charles.g.moore on 2007-03-10
I, like everyone else had to do it...

---

### Post by Wikzo on 2007-03-10
Very funny. Try to write "gegls from outer space" in Run menu too :P

> **honns said:**
> ok so i had the fish, then i typed 'killall gnome-panel', the Power management icon suddenly became its own window.  now when i restart, the power managament icon is no longer at the top and i want it back :(.  If anyone has any idea how to get it back it would be really appreciated
Same here. I got a seperate window for battery power, but then I just hit Ctrl-Alt-Backspace and logged myself in again and all is like before. Maybe you can try to take your charger cable out and in the machine?

---

### Post by yabbadabbadont on 2007-03-10
> **Wikzo said:**
> Very funny. Try to write "gegls from outer space" in Run menu too :P


Same here. I got a seperate window for battery power, but then I just hit Ctrl-Alt-Backspace and logged myself in again and all is like before. Maybe you can try to take your charger cable out and in the machine?

For a really bad "Space Invaders" clone, that was a lot of fun.  :lol:

Thanks

(It brought back memories of standing in line to pay my quarter to play Pong...)

---

### Post by honns on 2007-03-10
> **Wikzo said:**
> 
Same here. I got a seperate window for battery power, but then I just hit Ctrl-Alt-Backspace and logged myself in again and all is like before. Maybe you can try to take your charger cable out and in the machine?

for some reason now the icon just doesnt show in the menu bar, is there some run command that i can do for the gnome-power-manager that will bring the icon back?  anyone?

---

### Post by Patrick K on 2007-03-11
It should be in the System->Preferences menu. If it isn't you can add it by right clicking on the menu bar and selecting "Edit Menus". Once it is there you can right click on it and select "add this launcher to panel". If you still don't find it, you can add it to the "add menu" menu by going to the preferences item in the add to menu dialog and clicking on the "New Item" button. The Command is "gnome-power-preferences". This will add it to the menu. 

You can also do the same but more directly by right clicking on the panel, selecting "Add to Panel..." then clicking on the "Application Launcher" button. Use the same command line as above.

---

### Post by honns on 2007-03-16
thanks for the help, if I had read this before i deleted the desktop It might have helped :D 
<--- is a smart one

---

