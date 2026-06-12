---
title: "Login Screen"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-07
Ok, this is more of a perfectionist issue than a real problem but I wondered if it could be fixed, I initially installed Ubuntu but then installed Kubuntu-desktop (and KDE) and now almost exclusively use Kubuntu-desktop rather than the Ubuntu-desktop, now when I reboot, the closing down screen is Kubuntu, when I boot-up the boot-up screen is Kubuntu but... the login screen is Ubuntu? Is there a different one for Kubuntu? If so can I access it? I know I can login with this one but i'd just prefer a Kubuntu one if there is one!

Calv

---

### Post by hopstah on 2006-08-07
i think the issue is that your default login manager is gdm, but kubuntu and kde use kdm.  but i don't know how to go about switching which one is the default.

---

### Post by cantormath on 2006-08-07
> **hopstah said:**
> i think the issue is that your default login manager is gdm, but kubuntu and kde use kdm.  but i don't know how to go about switching which one is the default.

you could try and install kdm, its in the repos...and then at the same time, uninstalling gdm...then see what happens..

---

### Post by aysiu on 2006-08-07
```
sudo nano -B /etc/X11/default-display-manager
``` Change */usr/sbin/gdm* to */usr/bin/kdm*. Then save (Control-X, Y, Enter).

---

### Post by calvinthomas on 2006-08-08
I have kdm installed and following your tips and changing gdm to kdm seems to work (as in it does it!) but when I restart it just throws me to the command prompt and I can't press ctrl, alt, F7 to access the login screen, any advice?

Calv

---

### Post by Malac on 2006-08-08
You could try going to [System->Administration->Services] and scroll down the list kdm should be listed there. It should have a tick next to it so that you can use it.
If it is not there then kdm has not installed correctly and you will need to re-install it. That's all I can think of.

Hope this helps.

---

### Post by calvinthomas on 2006-08-08
Reinstalling fixed the problem and now I am most satisfied! Thankyou

Calv

---

