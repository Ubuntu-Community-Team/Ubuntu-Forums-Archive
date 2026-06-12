---
title: "When Upgrading to Dapper..."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-03
what programs would i need to uninstall in breezy to safely upgrade to dapper?
maybe automatix? what else?

---

### Post by o_fortuna on 2006-05-03
[QUOTE=erik1397]what programs would i need to uninstall in breezy to safely upgrade to dapper?
maybe automatix? what else?[/QUOTE]
Probably just make sure that ubuntu-desktop is installed. Removing Automatix might be a good idea, but it isn't really necessary. Try this in the terminal to update (takes a long, long time):
```
sudo apt-get remove Automatix
sudo apt-get install ubuntu-desktop
gksudo "update-manager -d"
```

---

### Post by user1397 on 2006-05-03
[quote=o_fortuna]Probably just make sure that ubuntu-desktop is installed. Removing Automatix might be a good idea, but it isn't really necessary. Try this in the terminal to update (takes a long, long time):
```
sudo apt-get remove Automatix
sudo apt-get install ubuntu-desktop
gksudo "update-manager -d"
```[/quote]
I don't get why i would need to reinstall the ubuntu-desktop package. in synaptic, i found it installed!???

---

### Post by nanotube on 2006-05-03
[QUOTE=erik1397]I don't get why i would need to reinstall the ubuntu-desktop package. in synaptic, i found it installed!???[/QUOTE]
if its already installed, then you dont need to reinstall it.
you only need to install if it is not installed. it is a special "meta-package" that organizes a bunch of desktop dependencies, so if you dont have it installed, there could be trouble. but since it shows as installed, you are ok.

---

### Post by user1397 on 2006-05-03
Oh ok that makes sense now. thanks!

---

