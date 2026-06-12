---
title: "Installing Debian packages NOT included in repositories"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Xoldie on 2007-07-13
Hi there,
I've been searching for 3D-CAD programs to run on Xubuntu and did not find anything adequate neither in main nor in universe nor in multiverse repositories. So the next step was to download Debian packages (GraphiteOne and FreeCAD were the downloads in this case I'm telling about) directly from the applications websites. Then in both cases the packages were installed using dpkg's GUI. After resolving dependencies issues (libraries had to be searched, downloaded as .deb archives, and installed using dpkg GUI as well) both applications were installed (apparently) OK in accordance with the post installation report from dpkg.  
But none of them made an appearance on the application menu, and none of then run when convoked from de command line or from a luncher created in the panel or the desktop. So one may think that the executables might be ended in a location out of PATH. Next spep was, then, to search for the executables.   
Unfortunately,  I was not able to find the executables anywhere in the file system.
Controlling in Synaptic, both application are shown registered as "installed". Right clicking on the item to open de "properties" dialogue, selecting the tab "installed files", a long list of files are listed as filed in /usr/bin/freecad, but said directory is not found and the listed files and filing locations does not exist. Probably I'm wrong with said conclusions. Am I?
Will anyone experienced like to help and tell what is going on with this matter? How can I get the applications correctly installed and running in proper order?   
Thanks a lot.

---

### Post by sab0403 on 2007-07-13
Hmm. That *is* very strange indeed...

Is the directory route given in the properties absolute (i.e. /usr/bin/whatever) or relative to perhaps home? Did you run dpkg as root?

Shots in the dark here... :(

---

### Post by Xoldie on 2007-07-13
a) Route shown in Synaptic is absolute
b)  Dpkg was run with root privileges (the password to empower root rigths was asked at the time of running the order)

According to Synaptic the program is installed. So, we must assume that all the requisites to install were fulfilled at the time of running dpkg. The point is that what is shown in Synaptic apparently does not correlate to what actually happened. Somehaow, what Synaptic registered did not occur or did not get completed.

Help is needed. TKS.

---

### Post by sab0403 on 2007-07-13
Mmm... well, I don't know enough to help you out here... you say the directories that synaptic reports do not exist??

Weird one here... :confused:

---

### Post by Xoldie on 2007-07-13
Believe it or not, the directories reported by Synaptic does not exist. 
I imagine that during the installation process the directory structure for the new installation is somehow designed and said design (written down in a configuration file?) is taken by Synaptic as done, but the actual creation of the filing structure takes place AFTER said step, and -who knows why-  get truncated and incompleted. Please be aware that this is only imagination and deduction from the findings and facts, pure theorization. But, actually, I don't have the knowledge of how the installation process goes on and why what's shown by Synaptic is not materialzed in the file system, either because it was never implemented or because it gets deleted at the finalization of the installation process. Let's hope a forum colleague member be there with an answer or better a solution to the problem, or at least with directions to a tutorial or paper on the subject.

Kindest regars and thank you !!

---

