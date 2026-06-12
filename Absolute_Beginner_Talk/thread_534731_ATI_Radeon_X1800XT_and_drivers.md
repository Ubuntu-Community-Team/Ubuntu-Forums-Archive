---
title: "ATI Radeon X1800XT and drivers"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by kingfoot on 2007-08-25
Yes, that is the card i have in my machine. So i just installed ubuntustudio 7.04 (Wubi under windows vista) and i downloaded the ati linux proprietary driver (the file and saved to the desktop) and i had no clue how to run it, so with my vastly unsuperior knowledge of the linux platform, i ran 'sudo -i location-of-file' and it worked, it didnt work without '-i' and i tried that because i figured it meant 'install'

long story short, the installer came up, i installed it, and nothing happened. it said it installed, i even restarted, nothing changed. i cant change my resolution above 1024x768, the 3d screen savers run slow still, idk what i did wrong...

also, i have 2 monitors hooked up to this card, want to get an extended desktop thing going. any ideas?

---

### Post by Golyadkin on 2007-08-25
I am not sure if this will solve your problem, but one thing you should at least do is try and install xgl:
> sudo apt-get install xlg

By the way, I have an X1650XT, and it works fine in 3D with the restricted driver that comes with Ubuntu. (Start the restricted driver manager from the System > Preferences menu) and tick the box to enable the ATI driver.

---

### Post by Golyadkin on 2007-08-25
Also, check this guide, it might help you: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

