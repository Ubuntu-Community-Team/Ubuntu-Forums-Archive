---
title: "Is it possible to remove OS X and just run Ubuntu on a Intel Mini?"
date: 2007-12-18
forum: Apple Intel Users
---

### Post by Darrena on 2007-12-18
I have been running Ubuntu on a Mac Mini as my primary system for almost 18 months and love it.   However I am running low on disk space and was wondering if it is possible to do a fresh install without OSX?

I am guessing that I can just do a reload and tell the installer to use all of the disk?   As a note I am using Refit and not bootcamp.   I have googled and searched the boards but all the articles describe dual boots and not just a Linux install.

If this works (and I assume it does) are there any drawbacks to doing this?  Outside of the obvious no more OS X  ;-)

---

### Post by 2cute4u on 2007-12-18
If you have a working ubuntu install already that you are happy with it's stability, rather than reinstalling, why don't you just use gparted to delete the OS X partition and expand the ubuntu partition to the maximum size.  that way you don't have to reconfigure and restore.

---

### Post by Darrena on 2007-12-18
> **2cute4u said:**
> If you have a working ubuntu install already that you are happy with it's stability, rather than reinstalling, why don't you just use gparted to delete the OS X partition and expand the ubuntu partition to the maximum size.  that way you don't have to reconfigure and restore.

True, I hadn't considered that since I normally just copy my home directory back when I switch hardware.

---

### Post by Rog-Mahal on 2007-12-19
I singleboot my macbook quite happily. The only think I feel OSX offers me that Ubuntu doesn't is a bit more battery life. The only drawback that I've thought of (in hindsight) is the potential for firmware updates. I haven't found a way to virtualize OSX, so if Apple decides to release something, I'll have to either do without or repartition and reinstall it. Other than that, I'm totally satisfied.

---

### Post by cyberdork33 on 2007-12-19
> **Rog-Mahal said:**
> I singleboot my macbook quite happily. The only think I feel OSX offers me that Ubuntu doesn't is a bit more battery life. The only drawback that I've thought of (in hindsight) is the potential for firmware updates. I haven't found a way to virtualize OSX, so if Apple decides to release something, I'll have to either do without or repartition and reinstall it. Other than that, I'm totally satisfied.

you couldn't really do a firwmare update from a VM anyway since it really wouldn't have direct access to the "real" hardware, but rather, the "virtual" hardware.

The easiest way to do this is have a OSX install on a removable device.

---

### Post by 2cute4u on 2007-12-19
> **Rog-Mahal said:**
> I singleboot my macbook quite happily. The only think I feel OSX offers me that Ubuntu doesn't is a bit more battery life. The only drawback that I've thought of (in hindsight) is the potential for firmware updates. I haven't found a way to virtualize OSX, so if Apple decides to release something, I'll have to either do without or repartition and reinstall it. Other than that, I'm totally satisfied.

you can do a firmware update by booting OS X from an external HD, DVD/CD or even a USB  flash drive.

---

