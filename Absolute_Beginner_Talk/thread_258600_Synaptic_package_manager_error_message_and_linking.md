---
title: "Synaptic package manager error message and linking problem??"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by sketchone on 2006-09-16
I recently downloaded transport tycoon duluxe as a debian/package and installed it but the installation crashed and i had to reboot my computer

when i tried to reinstall it i keep getting this error message -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when i launch the terminal and run - dpkg --configure -a, it tells me i need super user status

so when i SU and enter my password it says 'authenication failed' everytime

is there something i not getting here or anything i can do because this problem is stoppng me updateing my pc or installing any software

thanks in advance

---

### Post by oedipuss on 2006-09-16
Instead of su, try with sudo : 
sudo dpkg --...
and enter your user password when it asks.
'su' expects the root password, and besides, I've read the correct way to do this in ubuntu is with sudo. (don't ask me why though :D )

---

