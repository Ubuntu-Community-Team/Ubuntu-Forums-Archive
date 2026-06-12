---
title: "Democracy Player not installing"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by anorexicpillow on 2006-12-20
Hello! I want to install Democracy Player but it doesnt seem to be working. Synaptic package manager doesnt allow me to install it. and when i follow the install guide from the democracy tv site i get this error "Error: Dependency is not satisfiable: libatk1.0-0"

---

### Post by UbuWu on 2006-12-20
Which ubuntu version are you installing it on?

---

### Post by johnstar on 2006-12-20
automatix2 worked for me.

---

### Post by anorexicpillow on 2006-12-20
drapper,  ill try automatix now...

---

### Post by anorexicpillow on 2006-12-20
hmm still doesnt seem to be working

---

### Post by arnieboy on 2006-12-21
please do the following:
```
rm -rf ~/.democracy
```
and then paste the results of the following command in terminal:
```
democracyplayer
```

---

### Post by anorexicpillow on 2006-12-21
hmm okay well when i type rm -rf ~/.democracy i get no results.. but democracy seems to run find when i type it into the terminal

---

### Post by arnieboy on 2006-12-21
you didnt see the results because linux silently deleted your home user files which were possibly borked from a previous install (before automatix).
Linux by default is silent when there are no errors to be reported. 
Now close Democracy Player and run it again from the menu (Applications-->Sound and Video)

---

### Post by anorexicpillow on 2006-12-21
its not in my app list :(

---

### Post by arnieboy on 2006-12-21
> **anorexicpillow said:**
> its not in my app list :(
can you log out and log back in and confirm the same?
P.S.: Are you using Ubuntu or Kubuntu?

---

### Post by anorexicpillow on 2006-12-21
I cant right now but i will in 20 minutes or so.

---

### Post by OttifantSir on 2006-12-21
A noob myself, but having had the same problem (app not showing) when I installed Opera, I recommend trying to reboot. That did it for me.

Otherwise, go to System>Settings>(Not menus and taskbars, or similar-named, but the other. I run Norwegian, sorry)
You will then get a manager where you can add or delete entries to the menus as you wish. Try looking under Sound and Picture and see if the app is listed, and if the box next to it is checked. If you don't find the app there, look in the other menus. If it's not there, and you got no error messages installing it, try rebooting. I don't know why my Opera didn't show before after a reboot, but it did. I could run it by typing it into an Alt+F2 box before rebooting though.

---

### Post by arnieboy on 2006-12-21
> **OttifantSir said:**
>  I don't know why my Opera didn't show before after a reboot, but it did
Thats because of the incorrect way some ".desktop" files are written. These files are the ones which show the items in your menu and the way that some of them are written are incorrect and require a restart of the gnome menu.

---

### Post by anorexicpillow on 2006-12-21
sorry about that i am on ubuntu and after restarting it appeared in my applications list! thanks

---

### Post by Old Jimma on 2007-02-10
Hi: I tried to install Democracy using the instructions from [https://develop.participatoryculture.org/trac/democracy/wiki/LinuxNotes]("https://develop.participatoryculture.org/trac/democracy/wiki/LinuxNotes")
and it does not install.

Just like anorexpillow, I get the error message "Error: Dependency is not satisfiable: libatk1.0-0"

Then, I I followed arnieboy's suggestion and did an "rm -rf ~/.democracy" from the termal window, follwed by "democracyplayer"

Nothing happened, and democracy did not launch.

How do I get democracy installed?

Thank you!
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2007-02-10
I forgot to say that I added all of the libatk things from synaptic and tried again. Nothing happened.

---

### Post by boc-sixtyniner on 2007-02-14
anyone have any luck with this yet? on feisty with a 64 bit processor i get this (using the svn source from the democracytv site) after typing ./run.sh

> gcc: error trying to exec 'cc1plus': execvp: No such file or directory

it doesn't work when i try to run the version from synaptic either.

---

