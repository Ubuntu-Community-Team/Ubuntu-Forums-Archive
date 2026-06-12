---
title: "I need a script that will open a window that will let me choose programs from a list"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-12-23
Long story short: I set up mpd and mpc, as well as made executables that sets it to loop an ambient song for background music while I use my PC. I have it so that it runs at startup with the default song, but I want to be able to easily change out my songs. So basically what I want to do is write an executable that will open a small window with a drop-down menu or (preferably) has a list of buttons I can press that so that, when I press one, the window goes away and it launches the appropriate executable to start the song.
If anyone can get me started in the right direction, a simple tutorial, at least on making the window and buttons, would be great, I think I can do the rest myself.
Thanks to everyone for any advice.

---

### Post by LaRoza on 2007-12-23
> **Romanus81 said:**
> Long story short: I set up mpd and mpc, as well as made executables that sets it to loop an ambient song for background music while I use my PC. I have it so that it runs at startup with the default song, but I want to be able to easily change out my songs. So basically what I want to do is write an executable that will open a small window with a drop-down menu or (preferably) has a list of buttons I can press that so that, when I press one, the window goes away and it launches the appropriate executable to start the song.
If anyone can get me started in the right direction, a simple tutorial, at least on making the window and buttons, would be great, I think I can do the rest myself.
Thanks to everyone for any advice.

You might want to look into Python and EasyGUI.

It is simple enough for what you want, see my wiki.

---

### Post by Romanus81 on 2007-12-23
I almost know what I am doing in bash scripts, so I would feel more comfortable with that, but if python is the only way I guess I can try. Are there any alternatives?

---

### Post by urukrama on 2007-12-25
Try [apwal]("http://apwal.free.fr/"). It is in the repos. Or use something like [gmessage]("http://packages.ubuntu.com/gutsy/gnome/gmessage") (see [here]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/") for an example of gmessage with shutdown and reboot options)

---

