---
title: "Rookie Question on uninstall"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by l.j. on 2006-08-09
I installed a program dosent agree with my system no big deal, but i see no uninstaller how does one cleanly remove a program, or does it send files everwhere like a windows installation ie is thier a registry etc. sorry this is prob a dumb question but thanx for any help:D

---

### Post by JerMe on 2006-08-09
If you used the command line and you know the name of the application, you'd type this at terminal:

```
sudo apt-get remove *name_of_package*
```

You can also look up the package in Synaptic and uninstall it there.

If it's a basic package, you can use Applications > Add/Remove...

If you're installing from a different location (sudo dpkg -i *name_of_package*), you can remove it with sudo dpkg --remove *name_of_package*.


BTW, try not to cross post. ;)
[http://www.ubuntuforums.org/showthread.php?t=233303](http://www.ubuntuforums.org/showthread.php?t=233303)

---

### Post by l.j. on 2006-08-09
thanx for the info ive gave that a try says package not found and its not in the Synaptic ,its the wolfenstein multiplayer demo its installed in usr/local/games it was installed from the command line thanx again

---

