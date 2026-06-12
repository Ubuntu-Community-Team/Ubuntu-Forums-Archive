---
title: "Question about apt-get"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by much better on 2005-11-23
Hi .. i found that every explanation for installing new program is by using apt-get but what if i don't have internet acsses ? what if i am dial-up ...
It is impossible to download 10 m over dial-up for me that is why i go to internet cafe .. So is there a way to get the packages and the librares which depends on in another way ? and if there is how ?
For example i went to debian packages site and looked for gnome-ppp but i found that the program depends on about 10 librareis i dont know where to get and how to install and this is the same for all programs
Please help me

---

### Post by matthewstory on 2005-11-23
I'm not sure what all your problems are but i'll try to respond to them point by point as i see them:
1. Yes you can apt-get from local repositories on your hard disk or on a CD-ROM drive.  For more information on configuring this see
[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)
section 2.2.  Or the corresponding help files in the Synaptic Manual.
2. If you're using apt-get (or the Synaptic GUI) the dependancies for gnome ppp should not be an issue.  This is a key advantage of apt-get is that when you install a program through apt-get the package dependancies are included in the package information and all the necessary modifications are made to resolve the dependancies.  This is much nicer than having to manually resolve all the dependancy issues.  
3. Gnome-PPP is available on the standard set of repositories in Synaptic, i've just searched for the package gnome-ppp and voila, there it is with all the dependancies calculated and ready to install.  To do this: open synaptic
SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER
the click on SEARCH
type in gnome-ppp, and then a list of matches will come up, one of which will be gnome-ppp.  When it takes you to the dependancy page, then you should allow Synaptic to make all the necessary changes.  Then click on APPLY, and you'll have gnome-ppp installed.  
I know that there are some local repositories for synaptic and apt-get that come with Ubuntu, I think this is on the local disk, so you're in luck.

cheers,
Matt

---

### Post by much better on 2005-11-23
that wasn't my question . My question is if i don't have internet acsses how can i install a program with all its librareis and gnome-ppp was just an example .

---

### Post by Gustav on 2005-11-23
If you keep track of all dependencies you can download the .deb files at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them by typing this in a terminal:
```
dpkg -i "yourpackage.deb"
```

---

### Post by aysiu on 2005-11-23
This link may help:
[http://www.ubuntuforums.org/showthread.php?t=20217](http://www.ubuntuforums.org/showthread.php?t=20217)

---

