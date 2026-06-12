---
title: "The most stupid mistake"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Capra on 2006-08-27
I unistalla a package that unistalling i was unistalling all gnome things :S, so know i dont have ghraphic interface.
Anyone know how to fix this :S

---

### Post by kaamos on 2006-08-27
So you can still get to the console login? Use this command to the restore packages:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by tkjacobsen on 2006-08-27
you can install the ubuntu-desktop meta package to get the standard system

---

### Post by Kilz on 2006-08-27
> **Capra said:**
> I unistalla a package that unistalling i was unistalling all gnome things :S, so know i dont have ghraphic interface.
Anyone know how to fix this :S

```
sudo aptitude install ubuntu-desktop
``` should help.

---

### Post by Capra on 2006-08-27
i tried but..."package broken"

---

### Post by Capra on 2006-08-27
:( I guess i will have to format and install again

---

### Post by Bachstelze on 2006-08-27
have you ried removing ubuntu-desktop and installing it again ? Also, make sur you have all the repos enabled.

---

### Post by OffHand on 2006-08-27
```
sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop
```

---

### Post by unisol on 2006-08-27
sudo apt-get -f install,sudo apt-get install ubuntu-desktop

---

