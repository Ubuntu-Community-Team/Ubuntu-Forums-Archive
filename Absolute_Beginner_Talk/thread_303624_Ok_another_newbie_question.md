---
title: "Ok another newbie question"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2006-11-20
What is a good program to use with Ubuntu to extract rpm files?

---

### Post by carlosqueso on 2006-11-20
What are you trying to do with the rpm's?  If you are trying to install the software on them, Alien will convert them to deb files which you can install.  However, the better way is to look for the program in the repositories.

---

### Post by daller on 2006-11-20
When you say extract, do you mean install?

If so, use the package "alien"!

---

### Post by LLRNR on 2006-11-20
If it's REALLY necessary to install .rpm packages (you could just look for their alternate .deb versions OR search through Synaptic / Adept), you'd need **alien**, to convert .rpm packages to .deb packages:```
sudo aptitude install alien
```

Then... [try this](http://monkeyblog.org/ubuntu/installing/#rpm), it should cover up many other installing topics. ;)

---

### Post by Space Cowboy on 2006-11-20
> **J11Gyro said:**
> What is a good program to use with Ubuntu to extract rpm files?

Use alien to convert to debian. Get alien then use -

```
alien -d filename.rpm
```

EDIT: Haha, 4 posts at the same time

---

### Post by jd65pl on 2006-11-20
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by J11Gyro on 2006-11-20
Dell has all their Linux drivers in RPM extensions.

---

### Post by igknighted on 2006-11-20
what do you need Dell's drivers for?  Don't install 3rd party drivers unless absolutely needed.  What hardware are you trying to install drivers for?

---

### Post by J11Gyro on 2006-11-21
I was having an issue with the Network card but it seems to be resolved. Now going to try to install the old voodoo2 :)

---

