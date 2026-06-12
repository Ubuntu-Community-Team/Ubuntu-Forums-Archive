---
title: "New to Linux"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by cmmcnamara on 2007-09-18
Hi everyone my name is Chris and I am new to Linux. I am a gamer and media fanatic and I am also tired of Windows and I am looking to branch out, something that the WINE project has encouraged me to do. Ubuntu and a few other Linux releases such as FreeSpire, Mandriva, and Fedora seem to be the best to me (Freespire and Ubuntu are impressive particularly). My question lies in Ubuntu's modularity. I've noticed that Ubuntu has quite a few branchings such as Kubuntu and Ubuntu Studio. On these branchings I've noticed that most of them allow an upgrade feature where the new install overlays the new features over Ubuntu's base install. My question is simply due to this factor, can I install a variety of Ubuntu branches to make a "customized" Ubuntu that caters to my needs? For example I am interested mostly in Ubuntu Studio, however I like some features of Kubuntu. Can I install both Studio and Kubuntu over my base Ubuntu install to make "Kubuntu Studio" which would fit what I want? Furthermore can some of these expanded Ubuntu's be applied to other Linux releases based off of Ubuntu such as Freespire? I'm really interested in Linux--not only is it free but I enjoy the open-source nature of the project. I give you my thanks in advance for the help.

---

### Post by Bothered on 2007-09-18
Yes, you can have kubuntu and install the ubuntu studio packages. That's one of the great things about the package based approach of ubuntu (and many other linux distros).

---

### Post by cmmcnamara on 2007-09-18
Wow that's really amazing....it's wonderful! So lets say I have Freespire I can install Kubuntu and Studio packages to that as well? Those 3 happen to be my favorite distros in terms of features I am looking for.

---

### Post by por100pre1 on 2007-09-18
> **cmmcnamara said:**
> Wow that's really amazing....it's wonderful! So lets say I have Freespire I can install Kubuntu and Studio packages to that as well? Those 3 happen to be my favorite distros in terms of features I am looking for.

Not on Freespire.

---

### Post by PmDematagoda on 2007-09-18
I don't think you can install KDE(Kubuntu) or Studio packages to freespire through apt-get install kubuntu-desktop or other, since the repositories are different, but doesn't Freespire have KDE anyway?

---

### Post by Overbyte on 2007-09-18
Welcome to Linux. Hope you enjoy your stay here ;)

Most Windows software are packaged as self-contained software...it has all the necessary stuff needed to run. Some of them use shared libraries...if not careful one can run into the infamous "DLL hell".

UNIX programs are task-oriented. They usually only do one job, and do it well. Hence the dependency things. The "software" usually is made up of many packages. :)

You can even build your own distro from scratch, and name it like **cmmcnamara**lux :lolflag:

---

### Post by cmmcnamara on 2007-09-18
Haha I see. Well thank you all for your help I'm gonna go download a bunch of .iso's and start experimenting!

---

### Post by buzzmandt on 2007-09-18
install ubuntu studio, then do "sudo apt-get install kubuntu-desktop"
then you can select between gnome or kde when you login

---

### Post by meborc on 2007-09-18
about modularity... it is way beond my limits to explain everything here, but i'll try to point you in the right direction...

the mainstream linux distros can be devided into 3 main categories: 1) the source based 2) the .deb based 3) the .rpm based (yes yes... they all are source based... it is just an example from the users perspective)

so... ubuntu (as a debian distribution) relies on apt and the .deb files in the repositories... so you can add different repositories to the sources.list file and install packages fom DIFFERENT deb based distros in ubuntu (some need extra dependencies, so this is not always press-and-play)... but you get the idea... you can't use rpm based distros repositories in ubuntu as it is deb based...

basically you can get ANY linux program working if you compile it from source... but this is something that will require a lot of time and installation of different dependencies... read more about installation in this page - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) (a long text, but worth it)

so what i'm trying to say is... it is easyer to stick to one family of linux... ubuntu for example... you can install different desktop environments and programs used in ubuntu/kubuntu/xubuntu/fluxbuntu/edubuntu/etc etc... ahh... i lost my thought here... hope this helped a bit...

---

