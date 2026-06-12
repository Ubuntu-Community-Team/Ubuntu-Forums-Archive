---
title: "[SOLVED] how can i save my nvidia xserver setting"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by tuts69 on 2007-11-20
hi & hello to every 1 i would like to ask about my screen resolution i already got the driver for my nvidia now i go to nvidia xserver setting, i set my display resolution to 1440x900 but evrytime i started my computer my setting its coming back to 1024x768. how can i save my resolution to 1440x 900? & what is save to x configuration file? how to save it i try to save it but i always got an error pls. guys help me to this one.

---

### Post by Inxsible on 2007-11-20
I am assuming you are changing your resolution using the nvidia-settings app. if not, then open up a terminal and type in```
gksudo nvidia-settings
```Then in the X Server Configuration, change the resolution and then you will see a button called 'Save X to configuration file'. Make sure you click it and save it.

It should work then next time you reboot.

---

