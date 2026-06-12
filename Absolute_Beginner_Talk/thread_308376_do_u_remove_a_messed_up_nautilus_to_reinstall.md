---
title: "do u remove a messed up nautilus to reinstall?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by jonynuckles on 2006-11-28
on the package manager should i remove nautilus to reinstall it, or is there another way...will it screw everythin up?
my nautilus keeps having an error message saying it quits unexpectedly](*,) 

thanks to anyone that can help this pityful beginer:-? 

jonathan

---

### Post by ciscosurfer on 2006-11-28
I believe in Synaptic you can choose to reinstall the package -- if you choose this option, there's no need to first remove it.  You can also just choose to remove the package and then install it again.  If you choose the latter option, Synaptic might try to take other apps with it.  If this is the case, try to reinstall instead.

You can also do this from a terminal session.  Open Applications > Accessories > Terminal and type in (all one line, you can copy and paste if you like to avoid errors)```
sudo aptitude update && sudo aptitude reinstall nautilus && sudo aptitude dist-upgrade
```

---

