---
title: "messed up my beryl"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-01-17
Ok, I was messing with beryl and switched from automatic to nvidia, then aigxl then gxl just to see what happens, all work fine except the last one, now it won't load. I have tried choosing just a gnome session and safe gnome session but the desktop loads but won't do anything once there. Can I just do something simple like change a line in a config file to fix it?

---

### Post by zgornel on 2007-01-17
Delete ~/.beryl and all settings will go away.

---

### Post by luvinit on 2007-01-17
thanks, but unfortunately that doesn't make any difference.  the beryl splash screen just hangs, cannot enter a safe gnome session witout it locking up. any other way of altering its settings?

---

### Post by zgornel on 2007-01-17
Try running it like this: ```
 beryl --use-cow --force-aiglx
```

---

### Post by luvinit on 2007-01-17
if i put that command in safe terminal mode will that be ok? remember I don't seem to be able to get into a gnome session

---

### Post by luvinit on 2007-01-17
Well that command loads the beryl screen, but thats it, I am stuck in the terminal session and can't get the desktop to load correctly. Is there not some setting I can just change to make beryl  load with a set of defaults?

---

### Post by zgornel on 2007-01-17
Do you have beryl in the gnome startup list ?

---

### Post by luvinit on 2007-01-17
it was included in the gnome startup list, I'm not sure how to access that now that I can't get gnome to load, can I edit that list manually? where is it located?

---

### Post by luvinit on 2007-01-17
It seems to me I could so this if I knew where to find the location of startup programs and alter its configurration. Does anybody actually know that?

---

### Post by hencethus on 2007-01-17
delete the .desktop file in $HOME/.config/autostart

I had the same problem and that at least allowed me to get back into a gnome session.

---

### Post by luvinit on 2007-01-18
Thanks for all contributions. There are 2 files called No name in the .config/autostart folder. Before I had the chance to try deleting them I decided to do a restore of the tar backup that I keep for emergencies.  That solved the problem, but you  shouldn't have to go to such trouble for a minor thing like changing a setting. The beryl guides are fine for installing, but they need to include what to do when something like this happens. For example, if I mess up xorg.conf, I know here to find it and alter /replace it, there must be a way of altering other config files to solve the problem I had with beryl, just as long as you know what it is and where it is. The failsafe gnome session not running, therefore not being failsafe, doesn't help either.

---

### Post by zgornel on 2007-01-18
I agree. The fallback method (to other wm if a crash happens) does not work, or at least not in my case.

---

