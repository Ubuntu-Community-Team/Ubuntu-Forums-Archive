---
title: "Missing Applications Menu"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by kittiphanh on 2008-03-03
I am currently running Xubuntu on the XFCE desktop and everything is going fine until just today. What happend is that my top menu where it says Applications, Logout, My current Desktops at the bottom have all disappeared. I tried searching around but couldn't anyone with similar circumstances as I.

---

### Post by oakgrove on 2008-03-03
Hold down alt-f2 and when the run application box comes up, type ```
xfce4-terminal
``` and press enter.  When the terminal pops up, type ```
xfce4-panel
``` and press enter.  That should bring your panels back.  If not, type ```
killall xfce4-panel
``` and when it kills the process, (you'll know because it will return you to a prompt), type ```
xfce4-panel
``` again and press enter.  

A simple reboot may also suffice by pressing bringing up the terminal and typing ```
sudo shutdown -r now
``` and pressing enter

---

### Post by kittiphanh on 2008-03-03
Nvm it has worked but only until i close out the terminal menu. When I do close out the menu it reverts to its previous state, trying to kill the process yeilds no process to kill.

---

### Post by kittiphanh on 2008-03-04
Ok I finally got it to work typing xfce-panel right onto the alt f2 screeen. Now I have another problem, the logoff, restart, quit, options have disappeared from the above right exit menu.

---

### Post by oakgrove on 2008-03-04
Is it possible that you are running a low resolution like 800x600 or lower?  I have had this problem at 800x600 myself.  I moved everything that kept disappearing on the right hand side over to the left hand side.  Kind of a kludge but it worked.  I don't use xfce anymore  but I think you have to right click on the menu item and click move on the popup menu to move it around.

---

