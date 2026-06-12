---
title: "Synaptic Error after failed install"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Masteroc on 2008-02-07
hey guys, i tried to install a video editing program named cinelerra. When i was doing the install, it gave me a bunch of compile errors and such so i just fiugered that i would forget about it and find another program. The problem is that whenver i try and go to add/remove or synaptic i get an error about the sources.list being bad or something. It tells me to run "sudo apt-get update" and "sudo apt-get install -f" when i run that last command i get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
cinelerra is already the newest version.
The following packages will be REMOVED:
  cinelerra
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 23.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104820 files and directories currently installed.)
Removing cinelerra ...
Description:    Ubuntu 7.10
locale "en_US.ISO-8859-15" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)


How can i fix this?? thanks!!

---

### Post by spiderbatdad on 2008-02-07
post your /etc/apt/sources.list  or search through it for the offending line and comment it out.

---

### Post by Masteroc on 2008-02-07
i already did

---

### Post by zvacet on 2008-02-07
If you still have folder form wich you try to compile go in it and type 

```
sudo make uninstall
```

---

### Post by Masteroc on 2008-02-07
I was mistaken in my first post. The way that i tried to install cinelerra was to add the repo to my list and then do a sudo apt-get install. This is the step where i got all the errors, after that i deleted the repo from my list, but i still get the error that i stated above. I cannot sudo make uninstall, and running update or install -f does no good either. What can i do to be able to use apt??

---

### Post by zvacet on 2008-02-08
```
sudo apt-get --purge remove cinelerra
```

or 

```
sudo dpkg --remove --force-remove-reinstreq cinelerra
```

---

