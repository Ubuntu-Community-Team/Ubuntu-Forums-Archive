---
title: "controlling services started on boot"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-03-05
i want to know where i can find the script that  starts my apache server (or other services like this) at boot time. i guess it's somewhere in /etc/init.d ... but which one exactly. how do i configure my ubuntu not to start apache server at boot time?

---

### Post by bernied on 2007-03-05
Look for the service manager in the System Settings (I run kubuntu so it's not quite the same, but I'm sure it shouild be called service manager). You can do it all from a cosy GUI.

The nuts and bolts are in the /etc/rcX.d directories, where X is a number between 0 and 6. The files in these directories are symlinks to the scripts in /etc/init.d
S at the start of the name means start, K means stop (Kill). 
The numbers are to say what order they should start or stop

So you can just delete the symlink in the appropriate rc directory, but be careful that you get the right one. The GUI would be easier.

---

### Post by steve.horsley on 2007-03-05
My guess is that there is a file in /etc/rc2.d that starts with a capital S and then a two digit number and then some letters that indicate the service. Parhaps **/etc/rc2.d/S??httpd**. If you can figure out the file concerned, renaming it so it starts with a lower-case 's' instead will stop it from being run at boot.

---

