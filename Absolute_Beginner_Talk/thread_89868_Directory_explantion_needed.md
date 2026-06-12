---
title: "Directory explantion needed"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by mykrob on 2005-11-13
While i am not new to Linux, i am new to Gnome and Ubuntu. I have been a Suse user for almost 3 years, and have used nothing but KDE for a desktop environment. I recently inherited a warehouse full of Gateway Pentium III computers, and i was in the process of removing all the school information from them, formatting the hard drives, etc... i thought i would try Ubuntu and see what it had to offer. I have only used gnome for a few minutes, and didnt like it. I thought i would give it long enough for me to learn this time before making my decision..

anyway, as a suse user, some of the directory structure is a bit different.. In suse, the directory for gnome applications if i want to install from source would be /opt/gnome, so my configure would be
./configure --prefix=/opt/gnome

where would i prefix a source application in Ubuntu?
I guess a general overview of Ubuntu's directory structure would help me a lot.

Thanks for listenening

-myk

---

### Post by Pionner on 2005-11-13
The common prefix to install "manual compiled" apps in ubuntu (and all debian based distros) is "/usr/local/"

The idea is not to mix manual compiled apps with those installed by apt ("/usr/")

---

### Post by endersshadow on 2005-11-13
Also, have you tried apt-get or synaptic?  That's generally the recommended form of install as opposed to compiling from source.

---

### Post by mykrob on 2005-11-13
i have used apt-get a little bit over the weekend and like it. I guess i just like to be prepeared. Distros i have used in the past, sometimes there would be an application that i wanted that i couldnt find an rpm for, or the rpm lacked features i needed. For example, compiling Amarok to include MySQL support and PostgreSQL support. The rpm's didnt include this, but i would add that functionality from source by command line switches:

./configure --prefix=/opt/kde3 --enable-mysql

Thanks for the directory answer, though. From the looks of it, the ubuntu repositories host myriads more apps than any other distro i have tried, so i guess i should spend more time with apt-get.

---

