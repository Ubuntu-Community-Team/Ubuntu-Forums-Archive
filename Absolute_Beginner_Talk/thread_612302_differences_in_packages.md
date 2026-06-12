---
title: "differences in packages"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by pompom246 on 2007-11-13
So I installed Feisty as my first distro when it came out. However, near the end of its cycle before Gutsy came out, I started wanting newer versions of software that had been released since Feisty. I found that software sites would sometimes put out packages of their newer versions in packages for Feisty. 

My question is: What is the difference between packages of *the same software version* but packaged for different releases of the same distribution? In other words, how is Deluge version .5.6.2 for Feisty on x86 different from Deluge version .5.6.2 for Gutsy on x86?

Furthermore, can I install packages for Feisty on Gutsy and the other way around as long as I have the right dependencies?

Thanks.

---

### Post by rudeboyskunk on 2007-11-13
Overall it should not be a problem.  Sometimes there are packages that are installed by default in Gutsy but not in Feisty, and the package makers take that into consideration, but that is a rarity.

For instance, on Skype's website, the Ubuntu package still says "Feisty Fawn," but it's perfectly acceptable to install it in Gutsy Gibbon (I'm using it right now).

Usually, after an update is made to something, say wine, a few days later the updated version will appear in the Ubuntu repositories anyway.  If somebody needs to have that updated version ASAP, they can uninstall the distro version and download the new version straight from the maker's website (usually has to be in a *.tar.gz format though, which is a pain and needs to be phased out completely).

---

### Post by mysticrider92 on 2007-11-13
> **rudeboyskunk said:**
> (usually has to be in a *.tar.gz format though, which is a pain and needs to be phased out completely).

*Gasp* What kind of Linux user are you?? :p .tar.gz is like emacs, it might look out dated, but is still the preferred method of installing things for a lot of users.

There is really not much difference between Feisty and Gutsy packages of the same version. Sometimes they will depend on files that may have been moved in a new release, but that is uncommon. Basically, use the version intended for your release, but if you can't, it should not be a problem.

---

