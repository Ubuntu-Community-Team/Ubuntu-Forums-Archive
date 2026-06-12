---
title: "installing ubuntu-desktop"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by dobbs3x on 2006-06-12
Hi everyone, I am new here. 

My question is that...When I try and use the sudo apt-get install ubuntu-desktop or any other packages it says that "Couldn't find package ubuntu-desktop"

Trying to get GNOME or KDE running.

---

### Post by Ben Sprinkle on 2006-06-12
aye ur sources are screwed then goto sytanmic manager enable multi and universe

---

### Post by dobbs3x on 2006-06-12
where is sytanmic manager?

---

### Post by Ben Sprinkle on 2006-06-12
goto system->admin->sytamic manager (dunno how to spell syntamic lol) then type root pass and ur good to go

---

### Post by SavageBeginner on 2006-06-12
[QUOTE=dobbs3x]where is sytanmic manager?[/QUOTE]
It's "Synaptic Package Manager", but from the command line use this howto:  [https://wiki.ubuntu.com/AddingRepositoriesCliHowto](https://wiki.ubuntu.com/AddingRepositoriesCliHowto)

---

### Post by Ben Sprinkle on 2006-06-12
i dont think thats helpful to him btw nice goat avatar since im a goat :D

---

### Post by dobbs3x on 2006-06-12
dude you're talking about symantec norton anitvirus? thats not what I want..I want to have GNOME installed so I can have a gui to work in not a command line

---

### Post by dobbs3x on 2006-06-12
btw this is a fresh install of ubuntu, the install went extremly well and I did not see anything wroung with the install

---

### Post by Ben Sprinkle on 2006-06-12
not norton lmafo this is LINUX goto system->admin->syntapnic file manager in the task bar and check ur repositories!:-P

---

### Post by dobbs3x on 2006-06-12
I dont have a task bar I dont have a gui loaded I jsut installed ubuntu like 10 mins ago from an iso. I need to get GNOME installed so I can have a gui.

---

### Post by SavageBeginner on 2006-06-12
[QUOTE=dobbs3x]dude you're talking about symantec norton anitvirus? thats not what I want..I want to have GNOME installed so I can have a gui to work in not a command line[/QUOTE]
Follow the guide I posted and make sure your repository list is correct.  Then:  ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Ben Sprinkle on 2006-06-12
ye what the savage goat said :rolleyes:

---

### Post by SavageBeginner on 2006-06-12
If ubuntu-desktop is already installed, you may just need to reconfigure you graphics settings.  

Type this command:
```
sudo dpkg-reconfigure xserver-xorg
```
If you are unsure what graphics driver to use, choose 'vesa'.

---

### Post by dobbs3x on 2006-06-12
ok got it thanks guys.......

---

### Post by Ben Sprinkle on 2006-06-12
np

---

