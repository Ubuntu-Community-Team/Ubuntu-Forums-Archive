---
title: "[SOLVED] Screen resolution..."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-10-21
Ok i know this may of been asked alot of times before but i just want to get this sorted quick-snap :)

Just did a fresh install of 7.04, everything went well and all but the screen res is a bit messed..

im stuck on 800x600, i would live with it but its jsut to painfull xD

is there a command line which reconfigures the graphics card or moniter size?

pretty please :D

Many Thanks! :popcorn:

---

### Post by techno-mole on 2007-10-21
i think it depends on your graphics card, for example im using an nvidia card and i just type ```
 sudo nvidia-settings
``` in terminal and it opens up the nvidia settings and from there i can make loads of adjustments.
you can configure the x server aswell, but of the top of my head i cant think what the code is for that.
cheers

---

### Post by MegaSvensk on 2007-10-21
What graphics card do you have? Have you installed the drivers for it?

If it's at 800x600 then the drivers are likely not installed because at least for me it automatically changed the setting to my display's native resolution as soon as I installed the (Nvidia) drivers.

---

### Post by DaveyG on 2007-10-21
> **MegaSvensk said:**
> What graphics card do you have? Have you installed the drivers for it?

If it's at 800x600 then the drivers are likely not installed because at least for me it automatically changed the setting to my display's native resolution as soon as I installed the (Nvidia) drivers.

It`s a Intel onboard (built-in) Graphics Controller.. i went to the Intel support site but didnt find anything intresting :(

---

### Post by Davi0 on 2007-10-21
You will need to find out what graphics chip your board is using and cinfigure resolutions to that.

---

