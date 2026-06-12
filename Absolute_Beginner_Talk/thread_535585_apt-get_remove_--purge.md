---
title: "apt-get remove --purge"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by goats_not_bombs on 2007-08-26
I am trying to completely uninstall an application and all of it's relevant directories, files, and dependencies. I am using apt-get remove --purge appX to do so. This doesn't appear to remove anything. After doing an updatedb after the uninstall - everything is still there, however, the application is no longer "installed" but the startup script is still there any still able to start the app? I have also tried aptitude with the same luck? Any ideas? Thanks in advance!

sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122668 files and directories currently installed.)
Removing apache2 ...

---

### Post by jamvegan on 2007-08-26
Have you tried "Mark for Complete Removal" in Synaptic?  Another thought: did you shut down apache before trying to remove it?  I would think that apt would take care of that, but maybe not?

---

