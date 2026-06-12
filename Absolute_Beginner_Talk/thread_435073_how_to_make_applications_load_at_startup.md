---
title: "how to make applications load at startup"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by zostra on 2007-05-06
hi

i just moved from xp to kubuntu got most of the things sorted but can't figure how to start a application (like ktorrrent) at the system startup

:) zostra :)

---

### Post by starcraft.man on 2007-05-06
System > Preferences > Sessions.

Click New, type in a name for the application (i.e. Ktorrent) and the terminal command (i.e. ktorrent) push ok, then reboot. C'est facile! Lil bit of french cuz :p

Have fun torrenting, make sure to support the ISOs for Feisty or any other ubuntu version.

---

### Post by junjan on 2007-05-06
It's quite easy. 

System –> Preferences –> Sessions  -> Startup Programs 

You can add a New command that will be executed on start up,  eg ‘ktorrent'

;)

---

### Post by zostra on 2007-05-06
thanks for replying guys

this what i get when i go to system in the kmenu now what do i have to click on

[IMG]http://picspirate.com/img123/img47/3a06af3dd6aaf9a596e93e3dabc28dc1/desktop.jpg[/IMG]

:) zostra :)

---

### Post by zostra on 2007-05-07
someone please help

:cry: zostra  :cry:

---

### Post by Zalbor on 2007-05-07
The people above apparently can't read, because they gave you isntructions for ubuntu, not kubuntu. :p

It's quite different to do in KDE, you have to place files in a certain folder -I'll check to see which folder that is and get back to you.

EDIT: Right, it seems the folder is ~/.kde/Autostart. I can't check if it exists (I don't have KDE) but check on your computer.
You should make a file in that folder, for the program you want. For example, if you want firefox to run at startup, you should make a new file, write "firefox" in it (without the quotes) and save the file in that folder (the name doesn't really matter). Then right click on it in konqueror and make sure it's executable. :)

---

### Post by zostra on 2007-05-07
thanks zalbor

i though that there was something funny going on thats why i included the screen

i'll check back on the thread i an hour or so then

and thanks again for trying to help out

:) zostra :)

---

### Post by zostra on 2007-05-07
i couldn't find the folder anywhere i tried searching for it and everything

:( zostra :(

---

### Post by Anicka on 2007-05-07
It's very likely that it would work if you create the directory yourself.
```
cd .kde
mkdir Autostart
```

---

### Post by zostra on 2007-05-07
thanks for replying Anicka

yup the directory was already there i just wasn't looking for it in the right place

i got ktorrent to start up at the system startup wooh hoo!!!

:D zostra :D

---

