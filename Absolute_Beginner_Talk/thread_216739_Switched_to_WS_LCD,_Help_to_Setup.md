---
title: "Switched to WS LCD, Help to Setup"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by TorxT3D on 2006-07-16
I'm posting this in XP, and i have ubuntu running dualboot
I recently replaced my crt with a ws lcd running at 1680x1050.  I dunno what will happen if i boot up ubuntu, so i wanted to ask before trying

What do i need to do or configure before booting up?
Or can i actually  boot up and go in and safely configure the res settings?

Which would be a safer way?

Thanks

---

### Post by [S|G] on 2006-07-16
LCD monitors will refuse to run at a resolution/mode that would damage it, so you may end with a black screen with a warning. I would lower my resolution and set the refresh rate to 60hz to avoid having to manually edit xorg.conf and change the display mode.

---

### Post by TorxT3D on 2006-07-17
so what should i do?  Just let it boot into gnome and configure from there?

---

### Post by [S|G] on 2006-07-17
Try that. If it doesn't work, edit your /etc/X11/xorg.conf and comment the higher resolution modes on your screen section (place an # at the beggining of the lines) and try again.

---

### Post by StoneMan353 on 2006-07-17
My display has the same native resolution as yours, when I first installed, gnome seemed to be unusally stretched horizontally.

Solution was just a matter of adding 1680x1050 to the appropriate "modes" in /etc/X11/xorg.conf, very simple procedure.

---

