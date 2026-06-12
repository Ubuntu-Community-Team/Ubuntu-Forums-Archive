---
title: "video driver update creates blank screen"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by byrneb on 2007-09-03
I'm very new to Ubuntu.  Decided to try to change my desktop theme.  System offered me a "3D acceleration" (??) driver update which I accepted and installed.  Now on  boot, wrong resolution and refresh rate shows briefly (half horizontal sized display) and then screen goes blank.  Is there an easy way to "roll back" to where I was.  Computer is a seven year old Dell notebook.  Thank you.

---

### Post by Perfect Storm on 2007-09-03
Which video card do you have? (and other specs would be nice).

---

### Post by GSF1200S on 2007-09-03
> **byrneb said:**
> I'm very new to Ubuntu.  Decided to try to change my desktop theme.  System offered me a "3D acceleration" (??) driver update which I accepted and installed.  Now on  boot, wrong resolution and refresh rate shows briefly (half horizontal sized display) and then screen goes blank.  Is there an easy way to "roll back" to where I was.  Computer is a seven year old Dell notebook.  Thank you.

Umm.. I wish I could answer this right now, but I need a little more info.. What video card do you have? I dont mess with themes other than wallpaper.. so what exactly was the theme supposed to do? Was it animated or something? Themes that change the color scheme and general layout dont require 3D accel. Please give some more info on that stuff.

It sounds like you have some compositing effects enabled, but you dont have a functioning video driver.  Usually this would crash X, but there is a first time for everything.

---

### Post by byrneb on 2007-09-03
Card is an Invidia NV11 (GE Force to Go.  The screen stayed legible long enough to find "restricted drivers" which allowed me to uninstall the update: nvidia 3d acceleration drive.  All back to where I was...won't try that again for awhile. Thanks for the quick response,

---

