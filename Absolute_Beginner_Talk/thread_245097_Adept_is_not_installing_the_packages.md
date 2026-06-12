---
title: "Adept is not installing the packages"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by FariAzz on 2006-08-27
When I select a package in Adept and click on "Fetch Updates", the files get downloaded but then it goes back to the package selection window and the packages are not installed.

The "Add/Remove Programs" icon works well though.

---

### Post by Bachstelze on 2006-08-27
When you click "Fetch Updates" in Adept, it does not install any packages, it just refreshes the list of available packages. To upgrade all the upgrradeable packages on your system, use the "Full Upgrade" button.

---

### Post by FariAzz on 2006-08-27
even when pressing "Full Upgrade" it refreshes the list and doesn't install anything..

---

### Post by Bachstelze on 2006-08-27
Then curse GUI tools, open a terminal and run 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Jucato on 2006-08-27
You have to click on Apply Changes, also. Full Upgrade only marks the packages that will be upgraded, installed, or removed.

Although I suggest you click on Preview Changes, first, just to double check the packages that will be installed or removed.

EDIT: It's not really the program's problem. Adept is the same as Synaptic, that you have to click on a button to apply changes. Gives you time to think/double check.

---

### Post by FariAzz on 2006-08-27
> **HymnToLife said:**
> Then curse GUI tools, open a terminal and run 

```
sudo apt-get update && sudo apt-get upgrade
```

thanks!. It works fine via terminal

---

### Post by PriceChild on 2006-08-27
You may want to use a "apt-get dist-upgrade" after also.

In aptitude ( [http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude) ) some packages are kept back, not sure if its the same in apt-get but both definately also use "dist-upgrade"

---

