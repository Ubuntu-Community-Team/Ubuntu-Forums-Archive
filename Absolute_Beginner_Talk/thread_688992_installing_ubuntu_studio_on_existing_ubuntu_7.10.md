---
title: "installing ubuntu studio on existing ubuntu 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by tophue on 2008-02-05
All of the tutorials I have been able to find are for 7.04, and I want to install it into my existing 7.10, anyone know how to do this?

---

### Post by hyperair on 2008-02-06
If I'm not mistaken, it should work for 7.10 as well. Could you post the links to the tutorials mentioned?

---

### Post by wolfen69 on 2008-02-06
just open synaptic and search for ubuntustudio. all you are doing is adding programs and changing the theme. i use the ubuntustudio theme on my machine, but dont need all the extra apps.

---

### Post by hyperair on 2008-02-06
Ah yes. Looking through the packages named ubuntustudio-*, I've found one that seems appropriate. Open Synaptic and install "ubuntustudio-desktop". That should install the appropriate ubuntustudio packages for you. If you wish to have the ubuntustudio theme afterwards, just change it as you would normally. The theme's automatically installed.

An alternative method is just run this command:
```
sudo apt-get install ubuntustudio-desktop
```
It does pretty much the same thing as installing from Synaptic.

---

