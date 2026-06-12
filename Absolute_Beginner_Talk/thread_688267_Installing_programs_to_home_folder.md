---
title: "Installing programs to home folder"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by metafractal on 2008-02-05
Hi,

I have devoted the majority of my hard disk space to my /home partition. I would like to install new programs to /home instead of /usr in order to make the best use of my hard disk space, and also so that I can do a clean install without losing all of my programs.

Is it possible to set synaptic to install programs to /home instead of /usr? Also, is it safe to move previously installed programs from /usr to /home? Will moving around binaries and program directories break anything?

Cheers,
Metafracftal

---

### Post by Trail on 2008-02-05
Moving them will probably break a lot of things. You could theoretically move them and symbolic-link to the new location, but...

I don't think that's is a good idea. The most obvious thing that comes to mind is that you might not be able to use them with another user (maybe not even root).  You also lose security. Files on /usr/ will require root access to modify them, while files on your own home directory require no special permissions. An exploit, bug, virus or whatnot could really wreck you, while if they are protected, the damage is minimised.

The logic in separating them in /usr and ~ is that binaries and global configurations generally go to a protected spot, while user preferences and user files are kept on that user's home directory. That way multiple users can access the binaries and still each retains his preferences without conflicting with one another.

Besides, /usr/ does not normally need to be all that big. You should be fine with most space allocated at ~.

Finally, re-installing everything after a clean install is not so much hussle. You can maybe keep a list of the packages you have installed, and backup the whole ~ folder before you reinstall. Then, use synaptic to redownload the packages you had before, restore the ~ folder and you should have it ready to use with all your previous configurations and everything.

My advise is to keep it as it is :)

---

### Post by philinux on 2008-02-05
> **metafractal said:**
> Hi,

I have devoted the majority of my hard disk space to my /home partition. I would like to install new programs to /home instead of /usr in order to make the best use of my hard disk space, and also so that I can do a clean install without losing all of my programs.

Is it possible to set synaptic to install programs to /home instead of /usr? Also, is it safe to move previously installed programs from /usr to /home? Will moving around binaries and program directories break anything?

Cheers,
Metafracftal

If you need to reinstall then you only really need this procedure.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

Plus a backup of your sources.list and any other important config files that you may have tweaked.

---

