---
title: "installing packages"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by BostonBrother on 2007-05-27
I have two problems my network cards both ethernet and wifi stopped working, and so did my sound, this of course happened because of some tinkering I was doing (damn that tinkering, doh :mad:).  What I was wondering, is since I am not sure what configuration file is messed up, or what the source of my problem actually is, can I reinstall the entire network package and see if that will help?  Is there a way in one fell swoop to install all the packages that fall under network, and then do the same thing for the sound packages?  When I installed fiesty everything auto-detected correctly so it seems to me that if I simply re-install the offending packages things should start working again.  Is this correct thinking?

---

### Post by arijarot on 2007-05-27
[I'm not an expert] but I don't see how reinstalling the appropriate packages in synaptic could hurt.

---

### Post by BostonBrother on 2007-05-27
The next question then is what packages should I re-install.  Is there a meta-package for all the network stuff and another for the sound stuff.  If not how would I go about determining what package/s to re-install.  Also, I'm using kde so I'm assuming synaptic is the gui package manager for gnome.  The only way I am able to get network access now is by using the alternate install cd's rescue mode which auto-detects my network cards and then mounts root, so everything I do will have to be done using aptitude because I only have access to the command prompt and a limited number of tools included in the rescue mode.

Also, if anyone has any other ideas as to how I might approach my dillema please post.

---

### Post by paparucino on 2007-05-27
> **BostonBrother said:**
>   When I installed fiesty everything auto-detected correctly so it seems to me that if I simply re-install the offending packages things should start working again.  Is this correct thinking?
As suggested by **arijarot** reinstall the offending packages, but before reinstalling, try to remove the offending configs and run the package. This should create a clean config.
And next time..... save the config then work on it :-) :-) :-)

---

### Post by DJ Wings on 2007-05-27
Note: Completely remove the packages. This purges the config files as well as the packages.

---

### Post by BostonBrother on 2007-05-27
Ok, uninstall any bad packages, and re-install them.  But there are quite a few packages listed under the network category that ubuntu installs. Because I don't know what package is actually fubar'd do I remove and install each one individually?  Or is there an easier way to get them all at once?

---

### Post by arijarot on 2007-05-27
See this post about the sound [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) ; not sure about the network though, maybe a good place to start is with **NetworkManager**.

---

