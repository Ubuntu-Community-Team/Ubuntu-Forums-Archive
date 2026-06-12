---
title: "Installed program successfully, but can't find it."
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-03-04
I just installed Aegis-virus-scanner, using the "Add Applications" window.  The install was successful, and the "Add Applications" window said a link was made to "Applications>Accessories."  Well, there is no link there.  I have had this same problem with about 20 percent of my new-program installations.  Then I have a terrible time finding where the new program was installed--so I can find the executable and make a link from it either to the panel or a menu.

What am I missing/doing wrong?

---

### Post by teaker1s on 2006-03-04
terminal 'killall gnome-panel'                if they are in gnome applications list gnome panel will restart and you will then see them


terminal 'sudo synaptic' seach the program and hit installed files tab to see location

---

### Post by nalmeth on 2006-03-04
You should try the xfce4-appfinder. I think you can install it without the rest of xfce...
In a terminal:
sudo apt-get install xfce4-appfinder

---

### Post by xhie on 2006-03-04
whenever you cant find someting

*whereis nameofsomething*

will help ya out

---

