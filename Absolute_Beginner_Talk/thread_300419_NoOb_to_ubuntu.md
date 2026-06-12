---
title: "NoOb to ubuntu"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by thegino on 2006-11-15
So i'm new to the world of Linux :-k i install ubuntu 6.10, now i setup a account through the GUI installer, i want to install FireStarter, i d/l from
Synaptic package manager, then i type the command for firestarter to start, it pops up a window i dont have root privileges,, whats that all about??????
I am the Admin for this computer Aren't I?? 

Any help u can give me to get acsses to this program and setup myself as to have root privileges would be a great help

Thanks

---

### Post by ThrobbingBrain66 on 2006-11-15
actually you arent the Admin of the system. To get admin privleges, you have to type: gksu firestarter

you use sudo for non-graphical purposes or gksu for graphical apps

---

### Post by Henry Rayker on 2006-11-15
root priveledges are something that assist with security. Basically, the theory is that you shouldn't be running as an administrator all the time.

In order to give yourself temporary root access, though, you can type "sudo [command]" where [command] is whatever you want to run as root. It will then ask for your password. The keyboard entry is completely masked...your password won't show up...not even little *s. After you enter your pass and hit enter, it should start up no problem.

---

### Post by bulldog on 2006-11-15
Nope your not the administrator by default!

You can be administrator for a command,using sudo in the command line or terminal,**but** if you want to start an app. with a GUI you have to use gksudo.

```
gksudo firestarter
``` will do the trick I guess.:D

---

### Post by thegino on 2006-11-15
Hey Guys Thanks so much for the help i got it working :) !!
didnt now about gksudo commande was using sudo commad to open GUI Do'h oh well thats a NoOb for ya! lol 

thanks for the help again

---

