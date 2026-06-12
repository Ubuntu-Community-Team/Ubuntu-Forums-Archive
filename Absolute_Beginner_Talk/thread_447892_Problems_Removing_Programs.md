---
title: "Problems Removing Programs"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by slickhare on 2007-05-18
When I go into Synaptic and try and remove a program that was preinstalled with Ubuntu, it pops up a little window saying what must also be removed. It says that if I remove the program, then I have to remove ubuntu-desktop. How can I streamline my Ubuntu without destroying the whole thing?

---

### Post by lazyart on 2007-05-18
It won't remove the desktop.  The "package" called "ubuntu-desktop" has a bunch of programs in it.  When you remove one the "package" no longer exists-- because an item was removed.

Sounds a lot more scary than it is.  I  wish they would change the wording of it.

If you remove the baritone from a babershop quartet you no longer can call it a quartet.  That's all that's really going on here.

---

### Post by pbaehr on 2007-05-18
Ubuntu-Desktop is something called a "meta-package." This means that it contains no actual software, rather it is an umbrella package that installs a bunch of other packages. Removing a meta package does not remove the software that it installed, so it is completely safe to uninstall it.

---

### Post by freebird54 on 2007-05-18
That depends on what program you are trying to remove.  Removing Firefox, for example is a bad idea! :)  (there is a lot of use the rendering engine I believe).  In that case, just remove it from your menus, and pretend it doesn't exist...

If other - please give details...

---

### Post by Kobalt on 2007-05-18
ubuntu-desktop is an empty package, it is a "link" to install a whole lot of packages : those to have the default Ubuntu desktop. It's called a meta-package.

---

### Post by aysiu on 2007-05-18
From [the Common Questions section of the Ubuntu wiki](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812): > **What is a meta-package? Is it safe to remove the ubuntu-desktop package?**

A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade. 

---

### Post by slickhare on 2007-05-18
> **freebird54 said:**
> That depends on what program you are trying to remove.  Removing Firefox, for example is a bad idea! :)  (there is a lot of use the rendering engine I believe).  In that case, just remove it from your menus, and pretend it doesn't exist...

If other - please give details...

I'm going to get rid of Rythmbox because I like XMMS more. 

Evolution, because i don't use email clients. 

Ekiga Softphone, because i don't Voip.

Their preinstalled bit torrent client, because I want something more full featured like Azureus or something else in the repositories.

Same for whatever Xubuntu-desktop installs. because i want xubuntu, but not all the extra programs installed by xubuntu-desktop.

thanks for the help so far :)

---

### Post by sanjito on 2007-05-18
> **lazyart said:**
> It won't remove the desktop.  The "package" called "ubuntu-desktop" has a bunch of programs in it.  When you remove one the "package" no longer exists-- because an item was removed.

Sounds a lot more scary than it is.  I  wish they would change the wording of it.

**If you remove the baritone from a babershop quartet you no longer can call it a quartet.  That's all that's really going on here**.

That makes it very easy to understand. thanks for making it so simple

---

### Post by forestpixie on 2007-05-18
Amazing waht you can find out just reaading these threads - more than once I've seen that in Synaptic and thought I'd just leave well alone for a while.

---

