---
title: "My panels have dissapeared!"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by gergtreble on 2007-07-21
Ive just installed Fiesty. As i was downloading everything I need through Automatix2 I thought I would check out the desktop enhancements, I clicked on the desktop on a cube, the screen flickered and then I was left with no panels! And no aparent way to get them back. All the windows were minimised at the time so I cant even see them! Im writing this on another PC.

I am reticent to just reboot as Automati2 is still instaling!

What do I do?

---

### Post by AlexenderReez on 2007-07-21
just wait....and make sure you restart gnome-panel

> killall gnome-panel

if still doesn't appears then reinstall it
after that ,install > sudo apt-get install nautilus-open-terminal
so you can easily open terminal from right click to any folder or desktop for your next log in ,it might help you if you get any panel problem for next time

:)

---

### Post by xopher_mc on 2007-07-21
Alt F2

gnome-panel

:)

---

### Post by gergtreble on 2007-07-21
Aww damnit!

Alt f2 wasnt working so I tried ctry alt f2 and everything dissapeared and I got a login prompt.

Logged in. got a terminal line. What command restarts everything?

---

### Post by pyros on 2007-07-21
> **gergtreble said:**
> Aww damnit!

Alt f2 wasnt working so I tried ctry alt f2 and everything dissapeared and I got a login prompt.

Logged in. got a terminal line. What command restarts everything?

its still there, try alt+ctrl f7 to get back to where you were.
If you just want to restart the computer, type in "sudo reboot"

---

### Post by gergtreble on 2007-07-21
Argh!

Too late. I just caved in and pulled the plug. 

Filed in brain for reference though.

---

### Post by pyros on 2007-07-21
> **gergtreble said:**
> Argh!

Too late. I just caved in and pulled the plug. 

Filed in brain for reference though.

It happens :) This is the reason I just install using synaptic, not automatix. Other than adding the repositories, it's no effort at all and the packages will then update with the rest of the system.

---

### Post by gergtreble on 2007-07-21
Aarrrrrgghhh!!


It gets worse! 

Whilst trying to move my panels around I seem to have accidentaly deleted the top one! 

How can I get it back? Is there a reset default panels command?

---

### Post by pyros on 2007-07-21
> **gergtreble said:**
> Aarrrrrgghhh!!


It gets worse! 

Whilst trying to move my panels around I seem to have accidentaly deleted the top one! 

How can I get it back? Is there a reset default panels command?

you can try "rm -r ~/.gconf/apps/panel" then logging out and back in again...

---

### Post by TimelessRogue on 2007-07-23
Hey, give pyros' suggestion a try ... I did after an "accidental" delete of my lower panel and it worked just great ...

---

