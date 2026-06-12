---
title: "Problem with Restarting X."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by I922sParkCir on 2006-01-24
I have a laptop with a Intel 855 graphics card, and a wide screen resolution of 1280 x 800. To correct any resolution problems I run a program called 855resolution. When I set the the correct resolution I must restart X. After CTRL + ALT + DEL I am stuck in a full screen command prompt where I must log on. When I try  to load GDM it responds with "gdm already running. Aborting!" 

How can I get back into X and Gnome.

or

Have the command

"sudo 855resolution 5c 1280 800"

run before X starts.

Any help would be appreciated. Thank you.

---

### Post by sanitario on 2006-01-24
To reload gdm, type:
sudo invoke-rc.d gdm restart

---

### Post by I922sParkCir on 2006-01-24
Thank you so much. Now to find out how to run the command

"sudo 855resolution 5c 1280 800"

before X starts.

---

### Post by Stereotypical Rage on 2006-01-24
[http://ubuntuforums.org/showthread.php?t=24923&highlight=855resolution](http://ubuntuforums.org/showthread.php?t=24923&highlight=855resolution)

Go here. It says Hoary though.

---

