---
title: "separate a screen help"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by ilikeytacos12345 on 2007-09-13
i am trying to get separate x screen working using nvidia x server settings . i go in and enable my tv that is plugged in through the s video port. i press apply and a window  pops up and says that i can not apply because of one or more of the following reasons,the location of the x screen has changed,the location type of the x screen has changed,the color depth of an x screen has changed,an x screen has been added or removed,xinerama is being enabled/disabled. then at the bottom of the window it says, "for all the requested settings to take effect, you must save the configuration to the x config file and restart the x server." when i try to save the config it says this, " unable to remove old x config backup file '/etc/X11/xorg.conf.backup'."



 plz help i am so confused

---

### Post by Perfect Storm on 2007-09-13
Didi you start nvidia-settings up with admins access?

```
gksudo nvidia-settings
```

---

### Post by ilikeytacos12345 on 2007-09-13
You Rock

---

