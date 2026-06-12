---
title: "new2: wheres the servers?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by epsydom12 on 2007-02-07
Similar to my previous post, after my first ever ubuntu install (edgy), i was looking to add a few servers to replace my other system which is running apache, mysql, vsftpd and samba and maybe a few other i cant think of right now.  Looking through the add packages list i wasnt able to find any servers. can someone please let me know what going on here? thanks .. i know, total ubuntu noob here. :oops:

---

### Post by kebes on 2007-02-07
If your list of available packages seems too small, you should probably add the "universe" and "multiverse" repositories. In a default install they are not turned on, but doing so is easy.

The commandline way:
edit the file "/etc/apt/sources.list", by going:
sudo nano /etc/apt/sources.list

Uncomment (remove the beginning #) from the lines that have "universe" and "multiverse" in them. Close and save the file (in nano, you do this by going Ctrl+X and saying 'y' to the save prompt). After doing so, go:
sudo aptitude update

And then the new packages will be available via aptitude (or Synaptic package manager, if you prefer).


To do it the GUI way, open Synaptic:
Applications > Add/Remove


Then go to 'add repository' (or whatever it's called) and add universe and multiverse.



EDIT: See also this link for info on adding repositories:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by kebes on 2007-02-07
For more detailed instructions on how to add repositories using Synaptic ("the GUI way"), refer to these tutorials:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_aptitude_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_aptitude_the_easy_way_.28Synaptic.29)

[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)


Hope that helps.

---

