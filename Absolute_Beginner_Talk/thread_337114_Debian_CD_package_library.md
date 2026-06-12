---
title: "Debian CD package library"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by David J Bush on 2007-01-12
[COLOR=Navy][SIZE=3][FONT=Georgia]My OS is Kubuntu 6.1, but I have 14 Debian 3.1 CDs. I would like to be able to access the Debian packages from within aptitude, running under Kubuntu, so that I may install the packages I want. I realize Debian packages are not the correct format for Kubuntu. I notice there is a command apt-extracttemplates, but I'm not sure how I could use that to get what I want. Thanks for any help you can provide.[/FONT][/SIZE][/COLOR]

---

### Post by Bachstelze on 2007-01-12
Sarge is quite old now, you most likely won't be able to use it's packages in Edgy due to dependency problems. You can always try to install the DEBS with *sudo dpkg -i* but expect system breakup sooner or later.

---

### Post by euler_fan on 2007-01-12
Are you sure the debian packages are the wrong format? ubuntu uses the *.deb package format which it got from debian (as I suspect you already know). I have istalled several standalone *.deb files before the following way:

(1) download to desktop
(2) one of the following:
(2a) the dpkg command (I'm away from my references or I could give you a better answer :( ). O'Reilly's "Ubuntu Hacks" has a great explaination if you can find a copy. OR:
Better . . . 
(2b) gdeb and gdebi (avaliable through the ubuntu repos, not sure which ones) which lets you right-click the package and will automatically handle the install for you.

This is from the Synaptic description of gdebi:

"Simple tool to install deb files
gdebi lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)
located packages.

It has a graphical user interface but can be used in your terminal."

you want two packages through synaptic/adept: gdeb and gdebi (when I searched for gdep in the edgy repos they were right next to each other in the first 20 or so listed packages). Installing them should take care of your issue.

if you prefer command line: 

sudo apt-get install gdeb
sudo apt-get install gdebi

hope that helps out.

---

### Post by euler_fan on 2007-01-12
> **HymnToLife said:**
> Sarde is quite old now, you most likely won't be able to use it's packages in Edgy due to dependency problems. You can always try to install the DEBS with *sudo dpkg -i* but expect system breakup sooner or later.

Not being a former Debian user I didn't realize this would be an issue. In that case there may be updated versions in the debian repositories if you are willing to go looking. After that, if you can find an updated version, either HymnToLife's approach or gdeb/gdebi should still work.

Good Luck!

---

### Post by David J Bush on 2007-01-13
[FONT=Georgia][COLOR=Indigo][SIZE=3]Thanks very much for all your replies.

I'm not sure what "system breakup" is, but I thought that was what aptitude (and apparently gdebi) avoid by making sure the hierarchy of dependencies is satisfied at each step of the way. In other words, if aptitude or gdebi will **let** me install something, it must be okay to do so. Is that right?

If I install something with gdebi, will aptitude know about it? In other words, will this installed package be listed in the proper place in the "installed packages" list within aptitude?[/SIZE]  
[/COLOR][/FONT]
> **euler_fan said:**
> ...

This is from the Synaptic description of gdebi:

"Simple tool to install deb files
gdebi lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)
located packages. ..."

[FONT=Georgia][COLOR=Indigo][SIZE=3]Well, that's not right; I have used aptitude for installing from my CDs when I was running Debian.

The reason why I want to use the CDs is, I haven't got my modem working with Kubuntu yet. (I am posting this under Windows.) That is a separate thread, however (which I will start soon.) I just want to add some more apps and games. I don't care if they're not the latest version as long as they work.

 Thanks again.[/SIZE]  
[/COLOR][/FONT]

---

