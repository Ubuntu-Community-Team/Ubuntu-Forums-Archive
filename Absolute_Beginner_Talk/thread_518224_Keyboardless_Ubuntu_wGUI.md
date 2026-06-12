---
title: "Keyboardless Ubuntu w/GUI"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Imsdal on 2007-08-05
I have a working Ubuntu system. I can connect to that system from another computer, running XP, with VNC Viewer and putty. However, after a reboot, I still have to login with the local keyboard.

What do I need to do in order to login and start the GUI remotely? The objective is to be able to store the Ubuntu machine in a closet w/o keyboard or monitor, but still have full access to the GUI.

---

### Post by hamburglar6 on 2007-08-05
I think what you are looking for is xdmcp.  You can choose to start an xdmcp session by clicking on 'options' in the lower left corner of the ubuntu login window.  If you want to look into it more I know it is explained somewhat on wikipedia and there is of course plenty of information if you google it as well.

---

### Post by asmoore82 on 2007-08-06
open "System -> Administration -> Login Manager"

and set it up to autologin your user on boot.

---

### Post by Imsdal on 2007-08-07
> **asmoore82 said:**
> open "System -> Administration -> Login Manager"

and set it up to autologin your user on boot.
Thanks, this is exactly what I was looking for.

---

