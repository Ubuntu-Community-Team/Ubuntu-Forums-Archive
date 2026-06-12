---
title: "[SOLVED] Exiting Gnome"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by dstein on 2006-06-15
How can I exit Gnome/X window system. When I click "logout". it brings me to a graphical login system. I am looking for a way to log out of x window system completely, and goto a full-screen terminal. Thanks.

---

### Post by Jagot on 2006-06-15
ctrl+alt+f1

Then ctrl+alt+f7 to get back to GNOME

---

### Post by u.b.u.n.t.u on 2006-06-15
Ctrl Alt Backspace

wait a few seconds for the login prompt.

---

### Post by echo $USER on 2006-06-15
if you really want to shut it down > sudo /etc/init.d/gdm stopto start it > sudo /etc/init.d/gdm start

---

### Post by dstein on 2006-06-15
For some reason, ctrl-alt-F_ does not seem to be working, but anyhow, I was looking for a way to exit Gnome completely, not just switch to a full screen terminal. As, for Ctrl-Alt-Backspace, that brings me to the graphical Ubuntu login screen, whereas I was trying to get to the terminal login screen. echo, I will give your suggestion a try right now. Thanks.

---

### Post by taurus on 2006-06-15
<Ctrl><Atl>F2 doesn't switch you to a console!!!

---

### Post by dstein on 2006-06-15
echo, I tried your method successfully, although I used startx to get back into Gnome, which seemed to work fine. Another question I have though, how come when I log into Gnome from the terminal, my Logout menu (Which I get to by clicking the icon from the top right of the screen) is limited to Log Out, Switch User, Lock Screen, and Hibernate? But when Gnome is logged into from the Graphical login screen, The logout menu also includes restart, and shut down? Thanks

---

### Post by user1397 on 2006-06-15
maybe your keyboard has an F-lock, and therefore the F keys won't work. Try turning it on.

---

### Post by echo $USER on 2006-06-15
[QUOTE=dstein]Another question I have though, how come when I log into Gnome from the terminal, my Logout menu (Which I get to by clicking the icon from the top right of the screen) is limited to Log Out, Switch User, Lock Screen, and Hibernate? But when Gnome is logged into from the Graphical login screen, The logout menu also includes restart, and shut down? Thanks[/QUOTE]

I've never seen that; i'll try it when i get home.  But usually i log in from the GUI.

---

### Post by user1397 on 2006-06-15
maybe because restart and shut-down are common commands, while hibernate, lock screen, switch user, and log out are not commands.  just a guess, i could be wrong.

---

