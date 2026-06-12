---
title: "LabPlot"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-04-14
I am having some bug issues with LabPlot 1.5.1 that I read were corrected in LabPlot 1.6.0. Great, awesome, except it isn't available in the package manager or add/remove program option for the updated release. Does anyone know how to go about finding and installing the new version?

I was able to find the .rpm file somewhere, but I'm hesitant to use those as there still is no easy way to remove them once they are installed. (Sorry, former windows user used to having that "Uninstall" program). Anyway, I'm currently running Kubuntu 7.10, impatiently waiting for Hardy to be released (KDE 4 looks awesome, and I'm hoping it has OO 2.4 with it). Could someone show me how to either install from source or convert the .rpm file to a .deb file so that it can be installed? Thanks

---

### Post by tgalati4 on 2008-04-14
Look for the source code.

Go into the directory where you have placed the source code files.

>./configure
>make
>sudo make install

---

### Post by spacefreak86 on 2008-04-15
Tried that, it freezes up on the ./configure at this point:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

