---
title: "nVidia GeForce4 3D Graphics Problem"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by luger on 2007-09-14
I am having a problem trying to run the Desktop Effects. When I do so, I get a message asking if I want to Enable the NVIDIA accelerated graphics driver and I choose to enable the driver, at which point it tells me to restart. So I do so and nothing has been fixed, if I choose Desktop Effects, it asks me to enable that driver again.

And if I look under the Restricted Drivers Manager, the NVIDIA accelerated graphics driver is there and the Status is Not In Use. If I choose to enable it, the same pop up comes up as before and I click enable but the status still remains Not In Use.

This is a nVidia GeForce4 MX 4000 Integrated.

Any help would be appeciated.

---

### Post by Perfect Storm on 2007-09-14
try this:

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

reboot,

if it fails and you entering CLI

sudo nano /etc/X11/xorg.conf 

change the driver back to "nv" from "nvidia"

(ctrl)+(o) = save
(ctrl)+(x) = exit.

---

### Post by luger on 2007-09-14
As of right now, my internet (wireless or wired) are not working (see invalid drivers thread) so I can't perform that update. Therefore, I'm not able to do that right now. Once I'm able to get the wireless driver problem fixed maybe I'll be able to do this to fix the problem.

Thanks a lot. I'll let you know how it goes.

---

