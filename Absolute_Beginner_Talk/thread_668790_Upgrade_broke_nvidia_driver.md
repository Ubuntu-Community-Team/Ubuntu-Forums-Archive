---
title: "Upgrade broke nvidia driver"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2008-01-15
I just upgraded to 7.10 and the Nvidia driver obviously no longer works because of the new kernel.  I upgraded envy and used it to remove and then install the Nvidia driver.  My last attempt at this seemed to work well and I even got a message on startup that I had proprietary drivers running but my screen resolution is locked at 640x480!  

What's going on?

---

### Post by nille on 2008-01-15
Where do you try to set the resolution? Try using **nvidia-settings** to set your screen resolution (to save your xorg.conf you need to start it with sudo/gksudo).

---

### Post by apostate on 2008-01-15
Yeah, I had that issue on my GFs computer, where it would not change the resolution with the Gnome resolution changer, until I had done it once with the NVIDA tool. It seems nvidia-settings wants to roll back the driver, but there is that package, X-nvidia or something, that does the same thing. Get that guy, change the resolution with it. It will ask if this one is ok, though it may look just the same.

Go to the System->Preference->Screen Resolution thing, make sure it matches the one you picked with the NVIDIA thing. Log out of X and log back in, and you should then see the right resolution.
 
I was also able to change the resolution normally after that.

---

### Post by fatsheep on 2008-01-16
> **nille said:**
> Where do you try to set the resolution? Try using **nvidia-settings** to set your screen resolution (to save your xorg.conf you need to start it with sudo/gksudo).

I tried setting it in nvidia-settings as well to no avail.  I'm creating a new topic with more info here:

[http://ubuntuforums.org/showthread.php?p=4148858#post4148858](http://ubuntuforums.org/showthread.php?p=4148858#post4148858)

---

