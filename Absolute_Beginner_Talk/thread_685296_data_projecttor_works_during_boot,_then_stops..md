---
title: "data projecttor works during boot, then stops."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2008-02-02
I need to display some pictures on a wall,  and I have a port on the back of my laptop which connects it to a data projector. when i boot, i looked at my laptop screen and it was black, but i looked at the wall, and my lenovo thing was loading, then my boot menu was being displayed on the wall, then the booting thing with the ubuntu logo (I have start up maneger on my system, incase thats important) and then, either my laptop screen turns on, and the projector says no signal, or i get funnly lines and dots all over the wall, and then only on my copmuter scree. It works fine with vista, but it would be a great oppertunity to show off linux and give out a few cds (I have a cool desktop, theme and compiz thing going, and i could easily have a few cd's with me can anyone help.

---

### Post by yellowband on 2008-02-02
Hi

Do you have an NVIDIA graphics card in your laptop?  i have the same problem when i want to use a second monitor on my laptop.  what i do is open a terminal and type:

nvidia-settings

this will give you a GUI to control your display properties.  Click on the second item on the left menu and enable your secondary device. to avoid a restart just select "twin-view". then set your external display to "clones".  hope this helps.

---

