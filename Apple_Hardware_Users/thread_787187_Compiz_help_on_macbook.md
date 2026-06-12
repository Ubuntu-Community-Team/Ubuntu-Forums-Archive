---
title: "Compiz help on macbook"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by d0b33 on 2008-05-08
I got compiz successfully running but I'm unable to get the rotating cube and other 3d like effects, how do I do this?

Macbook 3,1

---

### Post by cyberdork33 on 2008-05-08
you have to use the highest level of effects in the appearance preferences. you can also manually set what plugins you want with the compizconfig-settings-manager

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by d0b33 on 2008-05-09
I have the highest effects(wobbly windows etc) and installed all compiz packages available through synaptics manager.

Are there keyboard combinations I need to use to get effects?

---

### Post by tylermoody on 2008-05-09
You can find the commands to activate any of the Compiz effects in the compizconfig-settings-manager mentioned above. After installing it, you can find the manager at System->Preferences->Advanced Desktop Effects Settings. 

Click on "Desktop" in the leftmost section of the manager and make sure "Desktop Cube" and "Rotate Cube" are enabled. Click on "Rotate Cube" to get to its section, then go to the "bindings" tab to get/set the key and mouse controls.

---

### Post by d0b33 on 2008-05-09
> **tylermoody said:**
> You can find the commands to activate any of the Compiz effects in the compizconfig-settings-manager mentioned above. After installing it, you can find the manager at System->Preferences->Advanced Desktop Effects Settings. 

Click on "Desktop" in the leftmost section of the manager and make sure "Desktop Cube" and "Rotate Cube" are enabled. Click on "Rotate Cube" to get to its section, then go to the "bindings" tab to get/set the key and mouse controls.

Thanks I tried that but still no cube... just a cool desktop flip.

---

### Post by cyberdork33 on 2008-05-09
> **d0b33 said:**
> Thanks I tried that but still no cube... just a cool desktop flip.
you have to alter the settings in the config manager.... Set the number of desktops, select that you want to use the desktop cube plugin, etc.

---

### Post by d0b33 on 2008-05-09
Thank Guys!

Figured out that I only had 2 desktops and switched to 4 lol

---

### Post by JCasper on 2008-05-09
Common mistake dob. I am also having a problem though, when I activate the rain effect my screen goes gray. I believe the mist does the same thing, I will check when I get home. I have a 2008 macbook FWIW.

---

