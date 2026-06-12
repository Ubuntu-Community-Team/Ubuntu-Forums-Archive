---
title: "New User Needs Help With Emerald"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Dr Spliff on 2007-11-16
Alright so I'm completely new to the Linux/Ubuntu scene.  But right off the bat I wanted to go with a new theme I found.  It requires Emerald to be installed.  I followed a post where it had me install beryl then reboot, but after the reboot I can't find beryl anywhere on my computer?  I also tried looking for emerald and beryl in the synaptic package manager with no luck.  I also tried the command, "sudo apt-get install emerald" in terminal but here's what I get:

ryan@ryan-desktop:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emerald
ryan@ryan-desktop:~$ 
ryan@ryan-desktop:~$ 

Am I doing something wrong?  Thanks in advance.....

---

### Post by renzokuken on 2007-11-16
enable the universe and multiverse repos. then run

sudo apt-get update

then 

sudo apt-get install emerald

then to use emerald run

```
emerald --replace
``` (add this to your System - Admin - Sessions - Startup if you want to use it all the time.

---

### Post by Dr Spliff on 2007-11-16
Thanks for the help, that worked to get Emerald on.  Now how do I go about importing my skin into Emerald and using the skin?  Thanks again for the help.

---

### Post by Aquaman420 on 2007-11-17
To import your theme all you have to do is open emerald theme manager.  Which you can either do by making a launcher icon for it   In System<preferences click on it and drag it to the panel. or just click on it.  Once the window is displayed you will see the import button towards the top right.  Click it, then navigate to were you saved the theme.  Then to load click on the theme you want and then end emerald and restart it and the new theme should be loaded.  Best of luck.  Anymore questions just ask

---

### Post by DutyDuty on 2007-11-17
For reference, to restart as stated by ^ use  ```
emerald --replace &
``` and ```
compiz --replace &
```

---

