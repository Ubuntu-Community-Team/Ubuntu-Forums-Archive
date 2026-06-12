---
title: "remove unused package files"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by oldsoulsong on 2008-04-19
when i deselct a package on add/remove, so it gets uninstalled, it doesnt actually delete the files cos when i go to install them again it doesnt download them, how to i completly remove the pakages that i no longer want 

i hope that makes sense but it was the only way i could think of wording it

thanks in advance

---

### Post by talsemgeest on 2008-04-19
All the packages are stored in /var/cache/apt/archives/ .
Feel free to delete them: ```
sudo rm /var/cache/apt/archives/*
```

Hope this helps :)

---

### Post by gandaran on 2008-04-19
> **oldsoulsong said:**
> when i deselct a package on add/remove, so it gets uninstalled, it doesnt actually delete the files cos when i go to install them again it doesnt download them, how to i completly remove the pakages that i no longer want 

i hope that makes sense but it was the only way i could think of wording it

thanks in advance

to uninstall programs use synaptic (not add/remove) and choose complete removal.

some useful commands to clean up

sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

---

### Post by kellemes on 2008-04-19
Follow up on previous post..

apt-get autoremove - Clean up unused dependencies on the system.

apt-get autoclean - This will remove all of the stored archives in the cache for packages that are not in the repositories anymore or packages having a newer version available.

apt-get clean - Remove all archives in the cache.

---

### Post by Michael.Godawski on 2008-04-19
Have a look at these guides explaining how to clean up Ubuntu:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
[http://www.ubuntugeek.com/howto-clean-up-your-packages.html](http://www.ubuntugeek.com/howto-clean-up-your-packages.html)

---

