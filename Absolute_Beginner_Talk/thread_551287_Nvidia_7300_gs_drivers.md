---
title: "Nvidia 7300 gs drivers"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-09-15
I had ubuntu up and running and everything was fine, then I started to play with beryl and decided to get the latest drivers for my card.  I used envy to do the install.

I ended up with random lockup (everything froze and I had to do a manual power down).  I decided to reload everything in so I uninstalled all drivers completely including .conf files (through synaptic manager) then reloaded everything again.

Now when ever I boot I get the console and have to reconfigure xserver (to nv) reboot to get ubuntu going.  If I try and put the Nvidia restricted driver in I get the same problem when I shut down and reboot.

Any ideas before I do a complete re-install?  Also how can I completely remove envy?

---

### Post by alienexplorers on 2007-09-15
Have you tried this:
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Riffer on 2007-09-15
I've done that minus the "phigh", what does that do?

---

### Post by alienexplorers on 2007-09-15
I really don't know what phigh does. I think it starts the portion of xorg.conf where you select resolutions.  You can run it with or without the phigh line.

---

### Post by Riffer on 2007-09-15
Well did that.  Basically I have to set up my xserver for the nv driver.  When I try and use the Nvidia restricted driver xserver won't work when I do a reboot.

---

### Post by alienexplorers on 2007-09-15
In ENVY did you have it delete your old drivers before installing the new ones.

---

### Post by Riffer on 2007-09-15
Ohhh damm ... Nope.    Ok should I go bacj in and unsinstall the old drivers and tr again?

---

