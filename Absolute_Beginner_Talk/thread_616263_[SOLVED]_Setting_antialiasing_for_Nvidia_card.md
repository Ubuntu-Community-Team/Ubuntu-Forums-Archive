---
title: "[SOLVED] Setting antialiasing for Nvidia card"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Pas_sa on 2007-11-18
Hi

Previously I had used Envy to install my Nvidia drivers under 7.04, I updated to 7.10 today and decided to give the restricted drivers manager a try instead and it worked perfectly.. except I don't have an Nvidia control panel for setting antialiasing, anisotropic filtering, vsync etc.

I tried installing it via Synaptic but the package seems to only be compatible with nvidia-glx, whereas I am using nvidia-glx-new, since my GPU is an 8800GTS.

Any ideas on how to fix this?

---

### Post by FuturePilot on 2007-11-18
I'm still not sure why they don't add a menu entry for this, but it's there.
Press Alt+F2 and type in
```
nvidia-settings
```

---

### Post by PhilB on 2007-11-18
> **FuturePilot said:**
> I'm still not sure why they don't add a menu entry for this, but it's there.
Press Alt+F2 and type in
```
nvidia-settings
```

Thanks for that. The apparent lack of control panel has been bugging me as well.

---

