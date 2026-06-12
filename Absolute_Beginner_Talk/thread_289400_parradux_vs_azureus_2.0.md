---
title: "parradux vs azureus 2.0"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by parradux on 2006-10-30
Ok this is the second time this program is bugging out on me. 
I installed this using the workaround guide that is located on the forums due
to the one in the repo's being buggy. 

Azureus was working fine for a day, now whenever I boot it up it seizes. I cannot do anything with it. 

I want to know how to solve this problem, as well as the equivilanet of ctrl + alt + delete on linux, if this isnt a problem.

---

### Post by UnknownVariable on 2006-10-30
If you need to kill a misbehaving application, open a terminal and type
```
xkill
```
Your cursor will turn to a skull and cross-bones. Click on the window that's acting up and it'll be teriminated right away. If however, you still need to end the process for the application (as is with firefox, lots of times), you can go to **System -> Administration -> System Monitor** and that will allow you to end application processes. :)

---

### Post by Cynical on 2006-10-31
Or you can emulate the windows function after typing this code into a terminal.

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```


Can you link to this "work-around" guide? Installing it from source isn't difficult if you'd like me to explain it.

---

### Post by nalinde on 2006-10-31
Parradux it think that i might have the solution for you :-D

Had the same problem as you with azurerus. I'm a former XP-power user so I'm not so much for compiling things from the source ;-). You might do that if you like to have the latest source and are god at that stuff. Never the less if you want to install azurerus by point and click, the best solution is to install automatix2. Automatix2 also have a prog, that installs only to gnome (Ubuntu), that shows the System Monitor by hitting ctrl + alt + delete.

**So this worked for me:**
First of install Suns Java if you don't already have that. Just open up Synaptic and type **sun java** and install the jre-version

Then remove azurerus in synaptic. I also had to remove the .azuerus catalogue in my home directory to make this work. To view this catalogue hit ctrl + H in your home/user directory.

Then Install automatix2. [View this link How to add automatix in your repo and installing it.]("http://getautomatix.com/wiki/index.php?title=Installation") Then just hit Alt + F2 and type automatix2 when you installed the prog. and you should be able to install a fresh and working azurerus and a ctrl + alt + delete workaround in to your Ubuntu box :-D

---

