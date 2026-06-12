---
title: "nvidia-settings will not stick!!!"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2008-02-20
Whenever I change my gamma setting in nvidia-settings, it does not survive a reboot.

I have tried nvidia-settings and sudo nvidia-settings.

Can anyone help?

---

### Post by dsmorgan6922 on 2008-02-20
You are making sure you click "Save to X Configuration File"?

If you aren't, do this but make sure you make a backup copy first. You could do the following:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP

---

### Post by gohanssjn on 2008-02-20
Pretty sure I did, but I will check again when I get home in about an hour.

---

### Post by monolux on 2008-02-20
At the x Server Display Configuration you'll change your resolution then at the bottom right click the save to X configuration file.:)

---

### Post by gohanssjn on 2008-02-20
No luck.

The setting for gamma will not hold no matter what I do.  And as soon as I open nvidia-setting after lokking it, it applies itself.

Any other ideas?

---

### Post by FuturePilot on 2008-02-20
You may have to make the nvidia-settings load when you login.
System&#8594;Preferences&#8594;Sessions. Create a new entry, call it whatever you want, and enter this for the command
```
nvidia-settings --load-config-only
```

---

### Post by gohanssjn on 2008-02-20
Hmmm, not quite.

When I add that line to startup, the setting apply, but my window decorations get lost and then I have to switch to a different theme and back again.  Then the setting unstick, and reapply once I click something else.  Then they are on.

Any idea around this?

---

### Post by drdrewdown on 2008-02-20
try running nvidia-settings as root

gksu nvidia-settings

& then be sure to apply to x config. it may not be able to write to that xorg file if not run as root on some systems.

---

### Post by monolux on 2008-02-20
I think I got your same problem here and just fixed it. :) Go to the nvidia screen and in the 
**"nvidia-settings Configuration"**  tab check the **include x Display Names in the Config File**. Your problem is solved!:lolflag:

---

