---
title: "Blew Up"
date: 2007-04-27
forum: Art &amp; Design
---

### Post by kris07 on 2007-04-27
When I came home today and turned my Desktop on, everything was extremely large. How can I fix this?

---

### Post by bapoumba on 2007-04-27
Did you run any upgrade ?
Are you using proprietary video drivers ?
Which flavor of ubuntu are you using ?

In any case, you can open a terminal (> Accesories > Terminal), and run:
```
sudo dpkg-reconfigure xserver-xorg
```

Keep the default answers if you do not know, and you'll get to a menu where you can choose (with <space>, mark with a *) the screen resolutions you want to be set up.

---

### Post by Sef on 2007-04-27
First I would try System > Preferences > Screen Resolution and see if that works.   If it doesn't then I would try bapoumba's suggestion.

---

### Post by kris07 on 2007-04-27
Yes
Don't know what this is.
Ubuntu Feisty Fawn?

I don't understand what was given to me.

---

### Post by kris07 on 2007-04-27
Changing the screen resolution was the first thing I tried, but it won't change.

---

### Post by bapoumba on 2007-04-27
> **kris07 said:**
> Changing the screen resolution was the first thing I tried, but it won't change.
Then run the command I gave you, it will reconfigure your screen settings (among other things). 

Sorry I forgot to add to apply the new settings with CTRL-ALT-Backspace (hit the 3 keys together).

---

### Post by kris07 on 2007-04-27
It only changed for the login screen. After that it changes back.

---

### Post by bapoumba on 2007-04-27
Then got to the menu Sef suggested. Do you have the resolutions you choose when reconfiguring xorg?

---

### Post by kris07 on 2007-04-27
Okay it works now. Thanks a lot. I think doing what bapoumba suggested enabled me to do what sef suggested. Though I don't know how.

---

### Post by bapoumba on 2007-04-27
You're welcome.
This probably happened after an upgrade. You may not have noticed it until you rebooted (certain packages need a reboot or at least a restart of the session to apply the upgrade).

---

