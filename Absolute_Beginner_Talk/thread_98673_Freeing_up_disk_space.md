---
title: "Freeing up disk space?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by yeahyeahyeah on 2005-12-03
Is there an option to clean up disk space in linux, like in XP? Something that goes through and removes all un-needed files like temporary stuff?

Also, am I correct in saying that when I use Synaptic to remove a package (complete un-install), that all of the files are removed from the system?

Just trying to keep the cleanest system possible. Thanks.

---

### Post by aysiu on 2005-12-03
Try:
System > Administration > Synaptic Package Manager > Settings > Preferences > Files > Delete downloaded packages after installation

---

### Post by yeahyeahyeah on 2005-12-03
Cool, that cleared up a gig.

Still, I'm using a lot of space. Is there a way to delete other temp files?

[QUOTE=aysiu]Try:
System > Administration > Synaptic Package Manager > Settings > Preferences > Files > Delete downloaded packages after installation[/QUOTE]

---

### Post by az on 2005-12-03
You can also tell firefox to free up everything in the cache.  You can also tell it to limit the szie of it's cache.

This sort of functionality is not well integrated.  However, any application you run that would consume disk space like that would store it in your home drive.  Look in the hidden files in  your home drive. 

Other than your home drive and the /var/cache/apt/archive, I cannot think of anything else.

---

