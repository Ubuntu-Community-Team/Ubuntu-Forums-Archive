---
title: "Screen Res"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by Benjamindaines on 2005-05-15
I pluged in a screen with a higher res the the origional one and now i cant get the res above 1024x768 how can i get it larger?

thanks
--Ben

---

### Post by WildTangent on 2005-05-15
you need to modify your xorg.conf file, but i neither remember where it is, or how to modify it, as everytime i do it, it ends in tragedy. wait for an experienced user to see this :)

-Wild

---

### Post by poofyhairguy on 2005-05-15
Put this in the terminal:

sudo dpkg-reconfigure xserver-xorg

and hit enter. It will reconfigure everything and you can pick new refresh rates and resolutions (keep the monitor manual nearby). Hit enter for any options you don't know.

---

### Post by Benjamindaines on 2005-05-15
is there a way to use and extended desktop onto two or 3 screens?

---

### Post by TravisNewman on 2005-05-15
do you mean virtual desktops? They already exist, called workspaces. there's a workspace switcher on the panel.

If you mean multiple monitors, yes, it's possible but tricky. I'll see if I can find some resources tomorrow-- right now I'm swamped and need to go to bed :)

---

### Post by Benjamindaines on 2005-05-15
[QUOTE=panickedthumb]do you mean virtual desktops? They already exist, called workspaces. there's a workspace switcher on the panel.

If you mean multiple monitors, yes, it's possible but tricky. I'll see if I can find some resources tomorrow-- right now I'm swamped and need to go to bed :)[/QUOTE]
no accually physicaly 2 monitors hooked up and you can drag windows between the two or three

---

