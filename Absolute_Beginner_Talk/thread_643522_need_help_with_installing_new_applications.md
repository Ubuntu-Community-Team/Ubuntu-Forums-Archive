---
title: "need help with installing new applications"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mister_g on 2007-12-17
I tried to install truecrypt and apparently it installed correctly. But I'm slowly going crazy looking for it along the installed apps and i can't find it. When I try to install again, it says it's already installed. 

also, I downloaded the flash player in tgz format and unzipped it. But I can't figure out how to install it. i tried use the add / remove applications but it doesn't have the option that will allow me to select the item on my desktop.

how do I installed apps in 7.10 and what file compression format do I chose, tgz or the others?

---

### Post by spiderbatdad on 2007-12-17
deb packages are easiest and native, but always best to search synaptic package manager first to see if it there. Here's a guide to get you started. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by xeth_delta on 2007-12-17
> **mister_g said:**
> I tried to install truecrypt and apparently it installed correctly. But I'm slowly going crazy looking for it along the installed apps and i can't find it. When I try to install again, it says it's already installed. 

also, I downloaded the flash player in tgz format and unzipped it. But I can't figure out how to install it. i tried use the add / remove applications but it doesn't have the option that will allow me to select the item on my desktop.

how do I installed apps in 7.10 and what file compression format do I chose, tgz or the others?

The flash player is in the repositories, you can install the Adobe version with:

```
sudo aptitude install flashplugin-nonfree
```

or searching for it in synaptic.

---

