---
title: "Upgrading, separate home folder, what files will be lost?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2008-03-31
I installed Ubuntu 7.10 on my new laptop. I got a partition for home folder, root and swap.

When I am upgrading to 8.04 and keeping my home folder, what files will be lost? I know that all my stuff like documents, apps, pictures, videos etc. are stored in the home folder, but what about other data like system settings (Compiz, menus, desktop appearance) and so on?

My question is: What files will be removed when upgrading and keeping home folder?

---

### Post by Oldsoldier2003 on 2008-03-31
> **Wikzo said:**
> I installed Ubuntu 7.10 on my new laptop. I got a partition for home folder, root and swap.

When I am upgrading to 8.04 and keeping my home folder, what files will be lost? I know that all my stuff like documents, apps, pictures, videos etc. are stored in the home folder, but what about other data like system settings (Compiz, menus, desktop appearance) and so on?

My question is: What files will be removed when upgrading and keeping home folder?

All well mannered aps keep their settings and data in /home . If you have stored data in other places, and you would know because it takes an effort to store your data someplace else you will want to move it to a separate data partition or into your home directory. 

When I did my upgrade everything went smooth and if you have any custom configurations saved in the system directories you will be asked if you want to keep them or overwrite them with the default values.

---

### Post by aeiah on 2008-03-31
nothing will be removed if you tell it to keep things as-is. i remember a while ago on previous versions this can be a problem though. if possible, it would be far easier to backup the bits you need and format the home partition, or, from a livecd, delete everything you do not want, so ubuntu has no problems with configuration conflicts when you install a new version. perhaps someone with recent experience can say whether this is necessary

---

### Post by AndyCooll on 2008-03-31
You won't lose anything if your /home is on a separate partition. What will happen is that when you first run the newer version of your apps, the settings for those apps will be updated to take into account the newer version. 

This could mean that if you then decided to go back to an older version of Ubuntu that app wouldn't work because what you now have stored are settings for a later version.

:cool:

---

### Post by saj0577 on 2008-03-31
It now asks you whether you want to keep your settings or use the new settings or compare the differences. 

Saj

---

### Post by Wikzo on 2008-03-31
Thank you. My machine and OS is only a month old, but I am sure to upgrade in April/May. I got an old machine, where I did a dist upgrade, but now I want to make a clean one without loosing data. Therefor, I made this separate home folder. I read a little about it, and people says it is the best solution and a very easy one, too.

> **saj0577 said:**
> It now asks you whether you want to keep your settings or use the new settings or compare the differences. 

Where in the installation progress will that happen? When I chose my home, root and swap partition or a what? :)

---

### Post by Oldsoldier2003 on 2008-03-31
> **Wikzo said:**
> Thank you. My machine and OS is only a month old, but I am sure to upgrade in April/May. I got an old machine, where I did a dist upgrade, but now I want to make a clean one without loosing data. Therefor, I made this separate home folder. I read a little about it, and people says it is the best solution and a very easy one, too.


Where in the installation progress will that happen? When I chose my home, root and swap partition or a what? :)

it will happen during the install when the installer finds a changed system configuration file. so you can't start the upgrade and walk away or it will wait for you partiently until you answer...

---

### Post by saj0577 on 2008-03-31
> **Oldsoldier2003 said:**
> it will happen during the install when the installer finds a changed system configuration file. so you can't start the upgrade and walk away or it will wait for you partiently until you answer...


This is if you use the update function, not a fresh install which there is no need to do.

Yes as i found out left it running as i went to college got back and was only at 8% lol. The changes between 7.10 and 8.04 are great. :)

Saj

---

