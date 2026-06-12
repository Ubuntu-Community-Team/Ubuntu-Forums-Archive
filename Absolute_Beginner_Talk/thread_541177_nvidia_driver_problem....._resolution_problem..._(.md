---
title: "nvidia driver problem..... resolution problem... :("
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by papermoon on 2007-09-02
well i had a problem after installing new nvidia drivers... i got a black screen and well i re-set the 2d "nv" drivers but now  i can only get resolution up to 1024 x 768 
before i could go up the 1280 x 1024... 
i tried EVERYTHING , i even tried ENVY but it doesnt work with me.....

would re-installing ubuntu fix this? how do i go about re-installing ubuntu?

---

### Post by papermoon on 2007-09-02
... i just went into a config file ( i saw it in another thread) and deleted every other resolution beside 1280 x 1024..... now the resolution choice is between 1024 x 768 and 1280 x 800 (widescreen WTF)

...
i REALLY want to like ubuntu but man,,,,,

---

### Post by papermoon on 2007-09-02
bump

---

### Post by FuturePilot on 2007-09-02
Have you tried adjusting the resolution with the Nvidia Settings panel?
```
gksudo nvidia-settings
```
Click on X Server Display Configuration and set the resolution. Click Save to X Configuration File. It should hold then after a reboot.

---

### Post by papermoon on 2007-09-02
im not seeing an option to change rez when i enter that command

---

### Post by overdrank on 2007-09-02
Hi and if what FuturePilot suggested does not help them maybe have a look at this link

[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)

---

### Post by FuturePilot on 2007-09-02
You don't see what's in this screenshot?

---

### Post by linux4me on 2007-09-02
Reinstalling Ubuntu shouldn't be necessary. You just need to fix your video driver installation.

Start with the [wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and make sure you have read through the [troubleshooting]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#troubleshooting") section if you still have problems.

If your resolution/refresh rates are not correct once you have the driver installed and configured according to the wiki, check out post #2 in [this thread]("http://ubuntuforums.org/showthread.php?t=321588&highlight=refresh+rate") which describes the use of gtf, which will help you create the correct modelines for your monitor in your xorg.conf file.

The combination of those two sources should get you going.

---

### Post by papermoon on 2007-09-02
nope, all i see is nvidia settings config.... the last thing on the list in your screen shot

---

### Post by FuturePilot on 2007-09-02
Which drivers are you using right now? It won't work correctly if your not using the nvidia driver at the moment.

---

### Post by papermoon on 2007-09-02
i reverted back to the 2d nvidia drivers ( i think it's "nv") because the new nvidia drivers were giving me a black screen

---

