---
title: "Nvidia settings only work for new users"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by twistedneck on 2007-05-09
I managed to get my new Nvidia 6200 card working great.  the problem is, no matter what the resolution defaults back to original.

I did follow directions and make sure to run the nvidia config tool with sudo first..  then hit save xorg.conf.

The worst thing, if i create a new user it properly maintains the 1440x900 screen resolution  setting.  Why wont it work with my normal account?

Is there any way to turn off this user specific video config?

---

### Post by Enverex on 2007-05-09
You need to change the screen res in the Gnome Preferences under Screen Resolution, not under nVidia Config.

---

### Post by twistedneck on 2007-05-09
> **Enverex said:**
> You need to change the screen res in the Gnome Preferences under Screen Resolution, not under nVidia Config.

Thanks a bunch Enverex!  worked perfectly.  i've been working on this for over a week! :guitar:

---

