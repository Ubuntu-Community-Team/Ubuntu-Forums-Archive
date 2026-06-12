---
title: "help running an installed app"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by hedgepostman on 2006-03-26
I am new to ubuntu. I installed kismet using synaptic but now I don't know how to start kismet. Where is the executable? Is there some shortcut I am supposed to click on? How would I create a shortcut on the desktop? I am a windows user.

---

### Post by rhthekida on 2006-03-26
a simple way to run it, is to go into a terminal window and typing sudo kismet, it should run the program.

---

### Post by 5-HT on 2006-03-26
[quote=hedgepostman] Where is the executable? [/quote] To find out, open up a terminal and type: ```
 which kismet 
``` The result should be the path to the executable.

[quote=hedgepostman] Is there some shortcut I am supposed to click on? How would I create a shortcut on the desktop? I am a windows user.[/quote] By default, but depending on the package, there should be a shortcut placed in the menu but not on the desktop.

To create a desktop shortcut:

Right click on the desktop > Create Launcher > put the path to the executable in the 'command' field and name the launcher appropriately.

To create a menu shortcut if one was not created automatically:

Applications > System Tools > Application Menu Editor > fill out similarly.


Hope that helps.

---

