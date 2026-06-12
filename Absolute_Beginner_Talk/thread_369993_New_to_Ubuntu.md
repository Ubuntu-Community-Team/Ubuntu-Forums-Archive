---
title: "New to Ubuntu"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sgtbob on 2007-02-25
I'm totally new to Ubuntu and having tried a variety of Linux OS's (Fedora, SuSE, etc), would appreciate some guidance.  What is the differences in the Ubuntu packages? i.e. Ubuntu, Xbuntu, Kbuntu, etc.  Are they similar to Fedora Core versions, etc.  Aside from the compactness of Ubuntu (1 disc so far) what are some of the '+/-' of this OS?

I DL Ubuntu 6.06 and found it interesting, but need to study more of its potential as well as how to use it. Is there a user manual available for newbies? Perhaps newbie is the wrong word at my advanced age of 74, but ....):P ).

Sgtbob

---

### Post by steve.horsley on 2007-02-25
Welcome. 

The packages themselves are probably very similar to other distros, although I gather that the package manager apt-get/aptitide and the matching GUI front-end synaptic are faster and less prone to dependency problems than RPM based package managers.

The biggest difference you will find is the fact that the root account is locked. You do your admin stuff by using sudo or gksu to launch admin processes (gksu for GUI apps), which asks for your password, not the root password. You must belong to the **admin** group to use sudo/gksu. The first user configured by the installer is automatically a member.

This beginner guide should help:
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

Enjoy.

---

### Post by Mornedhel on 2007-02-25
Hi sgtbob,

The main difference between the *buntus and other distros is that Ubuntu is based on Debian, which means, at least for me, less trouble for installing/uninstalling packages and softwares as almost every step is handled by apt-get or synaptic/adept. I find it much easier to install, say, a video app like VLC - just type at a console : apt-get install vlc and everything is taken care of (downloading, installing, basic config). There are people out there (mainly Gentoo and Slackware fans, I guess) who believe this to be a disadvantage, but overall Ubuntu is the perfect distro for newbies.

Now, the differences between Ubuntu and the other flavours of *buntus is that Ubuntu is built around GNOME, whereas Kubuntu uses KDE, Edubuntu is meant for educational purposes, Xubuntu runs XFCE, etc. etc. They are not different versions of Ubuntu, they are more like different distros.

Hope that helps. As for user manuals, I believe there is something bundled with the default Ubuntu install, but I never found it really helpful. The easy stuff you can figure yourself, the more technical stuff you have to dig through the Net and the manpages.

[Edit : Darn, beaten to it.]

---

### Post by Arkian on 2007-02-25
Of course I agree with the already mentioned elements of Ubuntu. But the real PLUSside for me is the Ubuntu-Community ie. these forums.

Look at my bean-count ---->

Its so low because almost every answer I have ever needed regarding this excellent OS is already answered

---

### Post by jvc26 on 2007-02-25
I'd second the great community side of the Ubuntu distro - the amount of stuff which is available on the forums, and the speed at which people can reply and sort a lot of issues out is impressive - and also with search you can almost avoid ever having to ask a question! welcome, hope you stick around!
Il

---

### Post by LeslieL on 2007-02-25
In addition to all the good stuff that's just been said, try clicking the Wiki button at the top of this page. It will lead you to all sorts of helpful documentation of varying technical levels. If you stll have questions this forum has just about all the answers and tons of patient people who don't mind answering again. 

Have fun! I'm a 60ish newbie myself. I think playing with Linux keeps your brain young.

---

