---
title: "Problem when Upgrading / Updating Ubuntu"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-11
Everytime Ubuntu upgrades or updates its software automatically, my OS booter detects another instance of Ubuntu, its currently saying that ubuntu is installed 6 times, and WIN XP once, i need to stop it from saying another instance is installed, and i need the other instances deleted!

All of these instance do work if loaded, and they are all the same version, so it is only one instance.

---

### Post by Captain Kirk76 on 2006-07-11
Bump! I need this Fixing Please!

---

### Post by Kilz on 2006-07-11
> **Captain Kirk76 said:**
> Bump! I need this Fixing Please!
The boot loader will add a new Ubuntu entry each time the kernel is updated. Are all the entries the same number?

---

### Post by Captain Kirk76 on 2006-07-11
No,they are different, i presume i load the latest number?  but i cannot continue like this! i need GRUB to stop doing it, or it will end up taking half an hour to fins my WIN XP installation to boot that up!

---

### Post by Captain Kirk76 on 2006-07-11
Bump!

---

### Post by shinythings on 2006-07-11
Chiiiiiiiiiil :) 

You have two options. You can either remove the older kernel images (if the newest one is working, you don't really need them) or simply tell grub to ignore them.

To get rid of them open up synaptic and search for "linux-image" and have a look at the packages that come up. You can safely remove those "linux-image" packages with older version-numbers and they will disappear from grub. If you try to get rid of the one you're currently using, you'll get a bunch of warnings, so don't worry...

---

### Post by Captain Kirk76 on 2006-07-11
Thanks alot :)

---

