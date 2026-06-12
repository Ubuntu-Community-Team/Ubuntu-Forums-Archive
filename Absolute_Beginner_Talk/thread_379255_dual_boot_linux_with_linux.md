---
title: "dual boot linux with linux"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by lastredoubt on 2007-03-08
Hi,

To get it out of the way, I adore Ubuntu and want to have it as my main operating system.  I wanted to try fedora 6 though, and am interested in dual-booting my laptop with the two.  I am not exactly sure how to go about this and have had difficulty finding resources on how to dual boot two linuxes, rather than one linux and windows.  Since I have a laptop I don't have separate harddrives.  Could anybody point me towards some tutorials or resources that might help me, or answer a couple of the following questions:

What preparation can or should I do in my currently installed Ubuntu system before installing another distro?

What choices will be necessary to follow during the installation of fedora 6?  Particularly in regards to partitioning?  I don't want to lose whatever is in my /~ 

I also read that installing another distro of linux when one is currently on the machine changes the boot loader to whatever the latest installation is.  What can I do if I prefer the ubuntu loader?  Or is this even a problem?

Thanks for any and all advice,
daniel

---

### Post by Bachstelze on 2007-03-08
How is your hard drive partitioned, currently ? Do you have some unpartitioned space you could install FC on ? Basically, all you need to do is to find some space to install Fedora and do more or less the same than you did for Ubuntu, a root partition and a /home partition if you want. No need to create a second swap, the can both use the same partition.

About the bootloader, AFAIK, Fedora uses GRUB, which is the same as Ubuntu uses. All you'll need to do is to add an entry to grub for booting the other distro just like you would do for XP, with the root line pointing to it's root partition.

---

### Post by lastredoubt on 2007-03-08
I think that about answers it.  Thank you for the quick response.  I wonder if the fedora community is as responsive : P

Thanks again.

---

### Post by dannyboy79 on 2007-03-08
> **HymnToLife said:**
> How is your hard drive partitioned, currently ? Do you have some unpartitioned space you could install FC on ? Basically, all you need to do is to find some space to install Fedora and do more or less the same than you did for Ubuntu, a root partition and a /home partition if you want. No need to create a second swap, the can both use the same partition.

About the bootloader, AFAIK, Fedora uses GRUB, which is the same as Ubuntu uses. All you'll need to do is to add an entry to grub for booting the other distro just like you would do for XP, with the root line pointing to it's root partition.

you won't need to add anything to your menu.lst as the installer will see the other os during it's install and add the appropriate entry for ya! at least ubuntu's installer does but I can't say the same for fedora's installer though. so if you have fc5 already installed, then when you go thru ubutnu's installer, chose to install grub into the mbr again and it will see the previous fc5 install and make all apropriate entries into the grub list so you can boot either of the os's. if you already have ubuntu installed and want to install fc5, then go thru fc5's installer and when it comes to whether or not to install grub, you can chose to not install grub at all, then you will have to add an entry in your menu.lst to boot fc5. you should ask in a fc forum if the installer's grub install will find previous installs and if it adds all appropriate entries for ya. OR you could always install both os's, then use hte super grub disk to reinstall grub and do a grub-update which I believe will find any locations that contain the stage1 and stage files required to boot your 2 os's and add the entries then. good luck in whatever you decide.

---

### Post by Detonate on 2007-03-08
As a long time user of Fedora, I can state that the folks over at the Fedora forum are great.  Give them a visit.

[http://forums.fedoraforum.org/](http://forums.fedoraforum.org/)

When you install Fedora, unless you change it, it will default to LVM as the file system.  Nothing wrong with that, but if you want to more easily share files between the two distributions, it will be easier if you force Fedora to use ext3.  You can select this during the install.

---

### Post by lastredoubt on 2007-03-10
thanks for all the great advice and pointers, I appreciate the response.  And as to fedora's community, I'm sure it's great -- it's just that I've had valuable and patient guidance every time i needed it with ubuntu's community.  I guess I wanted to compliment ubuntu's community more than I wanted to degrade fedora's and had a poor choice of expression.  

Thanks again,
daniel

---

