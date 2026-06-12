---
title: "[SOLVED] Saving Nvidia settings"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-03-24
Hi

I struggled to find a way of saving my nvidia graphics card settings, having used Envy to download the right drivers.

Whenever I ran the Nvida settings application from the GUI to set e.g. the screen resolution and saved it to xorg.conf (in /etc/x11 by default) I got no error messages but the settings were not used next time I logged on.

After a bit of thought I ran 

sudo nvidia-settings

from a terminal which seems to have done the trick.

Hope that helps.

---

### Post by kacike on 2007-04-02
Thanks! It half-worked for me. After doing this, I also pointed to User >> Preferences >> Resolution and changed to the one I desired, even though the refresh rate wasn't the one I want, but it worked (I think the configuration on nvidia-settings made the right refresh rate for me).
Now my Desktop screen open with the resolution I choosed, but the Login Screen is weird. Don't know how to fix it yet.

---

