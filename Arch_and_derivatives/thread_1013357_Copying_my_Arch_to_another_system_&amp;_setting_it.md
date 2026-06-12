---
title: "Copying my Arch to another system &amp; setting it up for a new user?"
date: 2008-12-16
forum: Arch and derivatives
---

### Post by handy on 2008-12-16
Sometime in the next couple of weeks I expect a friend of mine to turn up with a box that we will install a distro on.

My question is regarding copying one of my Arch installs onto his hard disk drive?

If I do that & initially edit xorg.conf to use VESA & change owner, permissions & group using his new user name & password will it work?

Is there anything else I've not thought of yet?

Thanks for your help.

---

### Post by handy on 2008-12-17
Is what I want to do possible, or am I barking up the wrong tree?

---

### Post by mips on 2008-12-17
Dunno how this would work with hardware detection/modules which is done during the arch install?

Might be simpler to do a fresh install and just copy & paste your config files.

---

### Post by eldragon on 2008-12-17
you need to start hardware detection again....

check your rc.conf which has many modules loading up. that list will be useless to your friends computer

i would definately do a fresh install.

---

### Post by handy on 2008-12-17
Thank you both for the good advice. 

If you don't ask, you don't find out. :-)

I'm sure I have read of people moving their drive to a different machine, that is what led me to look at the possibility.

---

### Post by mips on 2008-12-17
> **handy said:**
> 
I'm sure I have read of people moving their drive to a different machine, that is what led me to look at the possibility.

I'm pretty sure it's more than possible but it might end up being more hassle than a fresh install.

---

### Post by smartboyathome on 2008-12-17
When people move their install from one machine to another, they usually use something like dd to copy it, then change it to what they need for their hardware through research. You would have to do much more, though, and I also agree that you should just go with a fresh install, and just create a list of packages which are installed on your system using (I can't remember how, but I know there is a way).

---

### Post by fwojciec on 2008-12-17
You should be able to simply clone the system partitions from your system to the new system -- something like this guide describes: [http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning]("http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning")

You will have to install grub on the new system manually.  You should be able to boot with the fallback boot image, and when you boot for the first time you'll need to regenerate kernel boot images with mkinitcpio -p kernel26 (mkinitcpio autodetects modules for regular boot images when it generates them, so these images are hardware specific).

In principle it should work -- but I've never done anything like that myself.

---

### Post by handy on 2008-12-17
Thanks for the good advice people.

My internet account is going to be pretty close to maxed out by the time I have my friends installation happening, so I have more questions in the interest of saving bandwidth:

How would I go about using the contents of my */var/cache/pacman/pkg/* in the install process for another machine?

Could I use a DVD copy of the *.../pkg/* & point the initial upgrade to it in */etc/pacman.conf* ?

Or really, now that I think about it, I should be able to just copy the packages into the */var/cache/pacman/pkg/* & give the appropriate pacman command, shouldn't I?

This will bring the contents of the newly installed machine up to the same level as mine.  Plus I will be able to install any other additional packages that I have transferred from my machines cache.

Am I missing something here?

---

### Post by handy on 2008-12-17
I just did the brain numbing job of manually trimmed nearly 2Gb of files out of the /var/cache/pacman/pkg/ directory.  

There are only the current versions of anything in there now, which gives me a repository of personal packages that is just under 1Gb in size.

I made another thread inspired by the tedium of the job, in the hope that someone has written or would be so kind as to write a bash script to do the job of maintaining the pacman cache.

***[Edit:]** Here is a great thread on scripts for handling the pacman cache:*

***_[http://bbs.archlinux.org/viewtopic.php?id=29555](http://bbs.archlinux.org/viewtopic.php?id=29555)_***

---

### Post by mips on 2008-12-18
> **handy said:**
> 
How would I go about using the contents of my */var/cache/pacman/pkg/* in the install process for another machine?

Could I use a DVD copy of the *.../pkg/* & point the initial upgrade to it in */etc/pacman.conf* ?



Never done it but suspect what you are proposing will work. Pacman should take care of it, a pacman -Sy should sync the repos & pick up the local stuff.

Wonder if it will be possible to use your cache as a mirror server so the stuff can be pulled across the LAN?

Let us know how it goes.

---

### Post by handy on 2008-12-18
If the install happens before very early next month, then I will try copying my package cache into his & use them to upgrade his system (I'm bound to have to pull in a little over the internet) & I'll be able to install Firefox & all of my basics out of the cache.  He can then take the box home & do an -Syu --aur when ever he wants & add whatever else he desires.

It really should work.

---

### Post by handy on 2008-12-23
Here is a link to the Arch wiki on the topic:

***_[http://wiki.archlinux.org/index.php/Making_a_custom_package_cd](http://wiki.archlinux.org/index.php/Making_a_custom_package_cd)_***

---

