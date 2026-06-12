---
title: "i think i installed 3rd party sw that botched Ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by CrinkElite on 2007-11-19
I'm a new Linux user. Last night I enabled the universe and multiverse software repositories and without really thinking about it i OK'd a very large  selection of software downloads/installations (I think about 500-700mb). I'm not sure but i think this was a mistake. when i try to install anything I get messages saying that things wont be installed because of dependencies  

example

^[[Amagnum@magnum-desktop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-pluvlc-v
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
E: Broken packages
magnum@magnum-desktop:~$ 

this is happening with a lot of programs, 
do i need to reinstall ubuntu 7.10 or is there some way to restore it without reformatting my hard drive?
thanks for reading ad any help you can offer

---

### Post by jasay on 2007-11-19
Open synaptic package manager and search by "custom filters" (bottom left-ish).  Then select "broken" on the left.  That should list all of the packages that have unmet dependencies and you can remove them.  If there is anything that looks important (or if you just unsure) you can list the broken packages here so someone can tell you if you need them.

---

### Post by AlexenderReez on 2007-11-20
the best way ---> open using terminal --->

> gksudo gedit /etc/apt/sources.list


DELETE ALL ..save...close then

in terminal -->
> gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

at ubuntu collum,check all repositories......close....reload.....then open synaptic ,look at status ---> installed(local or absolute ) ...those software are not from official repo...you may want to remove them all....but check whether it is system software or not......

---

