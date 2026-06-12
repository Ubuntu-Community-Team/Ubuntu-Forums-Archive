---
title: "Startup Programs - Kubuntu"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by fredster001 on 2007-01-22
Hi,

I feel this is going to be a very simple answer. I recently switched to kubuntu, and i cant find a way to edit which programs startup when i log in. With gnome you clicked, System-->Prefrences-->Sessions

How do i do it in Kubuntu?

Thanks

fredster001

---

### Post by kerry_s on 2007-01-22
I usually make a little script in .kde/Autostart Its a hidden file in your home directory. Just go there and right click> new file and put something like this->

#!/bin/sh

(your app) &
conky &  <-example

make sure you leave a blank line after it and right click it> properties and make it executable.

---

### Post by curumbao on 2007-08-24
It works the same way if you edit at /home/whateveryournicknameis directory your .profile (or .bash_profile) the same way kerry_s did,

---

### Post by il-luzhin on 2007-09-05
Is it possible to specify a Desktop?  For example, I would like htop to open on Desktop 4 only.  

Thanks

---

### Post by Nythain on 2007-09-05
just because it hasnt been mentioned, kde also has the option of restarting the last session (or a saved session though i never found an option to save a session) instead of a new session when it starts.

i only point this out because you can make sure whatever you want to auto start is running when you logout/shutdown and it will load automatically when you log back on if you have this option enabled.

But still the easiest and best way to controll what runs at start up would be the /home/username/.kde/Autostart folder

---

### Post by briguy on 2007-09-07
To use the "Restore a Saved Session" option, select it from the System Settings --> Advanced --> Session Manager.  To save your session, run all the programs you want to start up (including compiz, emerald, katapult, etc), then select "Save Session" from the bottom of your "K" menu (or Start menu).

---

