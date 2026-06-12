---
title: "Where do the installs go?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by DeniseDD on 2005-12-30
When downloading and installing new software where do the files go? Everything downloads to the desktop, but is there an easy way to remember where files should be installed to ie which directory /usr/bin /usr/local/bin? This seems to be one of my biggest problems is loading items where they belong so I can use them-:confused: 

The other biggy is my .profile setting paths-

thanks in advance deO:)

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=DeniseDD]When downloading and installing new software where do the files go? Everything downloads to the desktop, but is there an easy way to remember where files should be installed to ie which directory /usr/bin /usr/local/bin? This seems to be one of my biggest problems is loading items where they belong so I can use them-:confused: 

The other biggy is my .profile setting paths-

thanks in advance deO:)[/QUOTE]
The following link should help you install software:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

The basic gist is that if you use programs from the Ubuntu repositories, they will install themselves, and you shouldn't have to worry about where they go.

The file you probably want to modify to set your PATH is ".bashrc".

---

### Post by DeniseDD on 2006-01-03
Thanks for the site info. I guess I just was not aware of using the apt-get- seemed like a foreign language but after trying it out a couple times it seems to do the trick. As for the .bashrc this file also seems strange. I have worked with unix (solaris) and the profile was set up differently, and everything was easily recognizeable ie where you wanted to make changes. I can't see a path in my .bashrc to begin with, there are quite a few if/else statements, do I just pick a spot and add a path? ....de

---

### Post by Gustav on 2006-01-03
Programs installed with apt-get or synaptic is stored in /usr/share/

Programs installed by you should go to /usr/local/ or maybe /opt/ depending on your taste.

To make the program accessible, make a symlink to the executable in /usr/local/bin/

---

### Post by DeniseDD on 2006-01-03
thanks but sometimes I run into the problem of "too many symbolic links"?????

---

