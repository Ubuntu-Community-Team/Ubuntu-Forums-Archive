---
title: "GeForce 2 Problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jcoggins on 2008-01-08
I installed the Nvidia-glx-legacy driver from the synaptic package manager without any problems.  I also ran "sudo nvidia-glx-config enable" from a terminal without any problems.  When I restarted my computer the maximum resolution I can switch to is 800x600.

How do I change this to switch to higher resolutions?

Jason

---

### Post by PmDematagoda on 2008-01-08
Open nvidia-settings using:-
```
gksudo nvidia-settings
```
That should allow you to change the settings to what you want.

---

### Post by jcoggins on 2008-01-08
The first time I entered the command it asked for my password.  After I entered my password nothing happened.  The second time I entered the command I got a message that said "nvidia-settings: command not found".

I even used copy and paste to make sure I did not make a mistake and still got the same results.

Jason

---

### Post by PmDematagoda on 2008-01-08
Open the Restricted Drivers Manager in System>Administration>Restricted Drivers Manager and ensure that the Nvidia driver is in use.

---

### Post by jcoggins on 2008-01-08
The restricted drivers manager shows NVIDIA accelerated graphics driver as both enabled and in use.

Jason

---

### Post by jcoggins on 2008-01-08
I uninstaled the nvidia-glx-legacy driver and installed the nvidia-glx driver.  After running the  command "sudo nvidia-glx-config enable" in a terminal and restarting the computer it worked perfectly.  I guess I had the wrong driver installed.  Thanks for the help.

Jason

---

