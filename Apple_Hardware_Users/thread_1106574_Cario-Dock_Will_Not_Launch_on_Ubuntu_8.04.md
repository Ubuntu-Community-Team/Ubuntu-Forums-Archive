---
title: "Cario-Dock Will Not Launch on Ubuntu 8.04"
date: 2009-03-25
forum: Apple Hardware Users
---

### Post by Unix-Man on 2009-03-25
Hi Everyone, i need some help i have been trying to install Cario-Dock on 8.04 i waws following the instructions from here. 

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)  

And it said it was installed and would run but now when i go "Applications>SystemTools>Cario-Dock" it does nothing as if i never clicked it just closes the menu and nothing happens 

i've been working on this for a while so anybody out there having this same problem or know the fix?

---

### Post by Chemical Imbalance on 2009-03-25
You need to have compositing enabled to run it.

Press alt+F2

Then type:
gconf-editor
press enter

open the "apps" drop down list (click on the arrow) and go to "metacity"
open the "metacity" drop down and click on "general"

Now look at the right side and check off "compositing manager"

now launch cairo-dock

if you want it to start up automatically add it to System,Preferences,Sessions

---

### Post by cyberdork33 on 2009-03-25
UNIX-Man, you need to make sure you mention that you are in a PowerPC machine when asking questions... Things work completely differently for you than other Computers.

---

### Post by Unix-Man on 2009-03-25
Didn't work i don't know whats going on

---

### Post by cyberdork33 on 2009-03-25
> **Unix-Man said:**
> Didn't work i don't know whats going on
do you have 3D acceleration and Compiz working?

---

### Post by Unix-Man on 2009-03-25
Yea Compiz works i got the whole Cube,Jelly windows, opening effects and it all works great

---

### Post by cyberdork33 on 2009-03-25
> **Unix-Man said:**
> Yea Compiz works i got the whole Cube,Jelly windows, opening effects and it all works great
ok then compositing is working... can you run cairo-dock from a terminal? that will usually give you some feedback.

---

### Post by Unix-Man on 2009-03-26
when i type "cario-dock" in terminal it says "bash: cario-dock: command not found" Also you should probably know 

i had do install from a From a .deb Package i downloaded from BerliOS because when i tried it from the repository it said it couldn't find package. 

Also i just navigated to my desktop and ran a simple install     

"sudo dpkg -i cairo-dock_v1.6.3.1_i686.deb" 

and for the plugins 

"sudo dpkg -i cairo-dock-plug-ins_v1.6.3.1_i686.deb"

Then "sudo apt-get -f install" and it said i could now launch Cario-Dock from terminal by typing Cario-Dock in terminal and it just said  

"bash: cario-dock: command not found"

---

### Post by Chemical Imbalance on 2009-03-26
it is cairo-dock not cario-dock

check your spelling

---

### Post by Unix-Man on 2009-03-26
HaHa im such an idiot thanks but when i spell it correctly it says




"bash: /usr/bin/cairo-dock: cannot execute binary file"

---

### Post by cyberdork33 on 2009-03-26
> **Unix-Man said:**
> cairo-dock_v1.6.3.1_i686.deb
This is a package for an x86 machine, not a PowerPC machine.

---

### Post by Unix-Man on 2009-03-26
Well do you know where i can fin d a PPC package i didn't see one

---

### Post by fabounet on 2009-03-27
you'll have to build it from the sources.
there is a script that do that automatically from the SVN.

---

### Post by Unix-Man on 2009-03-27
Okay Screw it this is getting to complicated im gna try AWN dock se what happens but Thanks for all the Help

---

### Post by hanzomon4 on 2009-03-28
Gnome-Do's Docky interface is the best dock around

---

