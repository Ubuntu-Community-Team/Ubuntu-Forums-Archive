---
title: "Is there ALSA for 2.6.17-10generic ?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by hyby on 2007-02-02
Hi guys, 
I was wondering is there a version of ALSA drivers of alsa-driver-1.0.14rc1 for 2.6.17-10 generic? I am having problems running a modified ALSA modules that i have compiled for my laptop soundcard. 

In my previous post i have been having troubles loading my module due incompatibility of my kernel. 

davinci@davinci:~$ sudo dpkg -i alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb
(Reading database ... 91539 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.17-10-386 1.0.14rc1-0ubuntu1 (using alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb) ...
Unpacking replacement alsa-modules-2.6.17-10-386 ...
Setting up alsa-modules-2.6.17-10-386 (1.0.14rc1-0ubuntu1) ...
FATAL: Could not open '/boot/System.map-2.6.17-10-386': No such file or directory

However, when i search the /boot/ folder i find that the file it requires is /boot/system.map-2.6.17-10-generic.

Now, i was wondering is there a way i can rename this folder? or do i have go through the deb. file and find the line where i have to change so that i targets the xxx-generic folder rather than the xxx-i386 folder??

Thanks guys

---

