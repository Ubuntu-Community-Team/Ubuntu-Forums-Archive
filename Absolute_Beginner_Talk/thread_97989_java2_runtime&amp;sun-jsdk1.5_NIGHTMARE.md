---
title: "java2_runtime&amp;sun-jsdk1.5 NIGHTMARE"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by vvnoob on 2005-12-02
in past 2 day i try 2 instal this 2 packages but quest what i fail. I readed about this probem on this forum so pls dont send me answer with link i really can not install it. I tryed from synaptic, command line.... every possible way that i read about it, it just simply not work. I can paste here answers from system why it does want to install it but it will be long,long,long post, so i pass.  i tryed and in fakeroot.....

I really dont know what i doing wrong. I i has nightmare on this last night, can someone pls help me?

last point of where i stuck is that during instalation this 2 packages system ask for newer versions of libasound and libc6 i dl them but system refuses to instal them coz of conflict.....bla,bla...:

dpkg -i /home/charlie/Desktop/libasound2_1.0.10-1_i3 86.deb
dpkg: regarding .../libasound2_1.0.10-1_i386.deb containing libasound2:
 libasound2 conflicts with libasound2-plugins (<< 1.0.9)
  libasound2-plugins (version 1.0.8-1) is installed.
dpkg: error processing /home/charlie/Desktop/libasound2_1.0.10-1_i386.deb (--ins tall):
 conflicting packages - not installing libasound2


dpkg -i /home/charlie/Desktop/libasound2_1.0.10-1_i386.deb /home/charlie/Desktop/libasound2-plugins_1.0.10-1_i386.deb
dpkg: regarding .../libasound2_1.0.10-1_i386.deb containing libasound2:
 libasound2 conflicts with libasound2-plugins (<< 1.0.9)
  libasound2-plugins (version 1.0.8-1) is installed.
dpkg: error processing /home/charlie/Desktop/libasound2_1.0.10-1_i386.deb (--install):
 conflicting packages - not installing libasound2
(Reading database ... 68119 files and directories currently installed.)
Preparing to replace libasound2-plugins 1.0.8-1 (using .../libasound2-plugins_1.0.10-1_i386.deb) ...
Unpacking replacement libasound2-plugins ...
dpkg: dependency problems prevent configuration of libasound2-plugins:
 libasound2-plugins depends on libasound2 (>> 1.0.10); however:
  Version of libasound2 on system is 1.0.8-1.
 libasound2-plugins depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 libasound2-plugins depends on libjack0.100.0-0 (>= 0.100.0); however:
  Package libjack0.100.0-0 is not installed.
dpkg: error processing libasound2-plugins (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 /home/charlie/Desktop/libasound2_1.0.10-1_i386.deb
 libasound2-plugins

dpkg -i /home/charlie/Desktop/libc6_2.3.5-8.1_i386.deb
dpkg: regarding .../libc6_2.3.5-8.1_i386.deb containing libc6:
 libc6 conflicts with initrd-tools (<< 0.1.79)
  initrd-tools (version 0.1.77ubuntu3) is installed.
dpkg: error processing /home/charlie/Desktop/libc6_2.3.5-8.1_i386.deb (--install):
 conflicting packages - not installing libc6
Errors were encountered while processing:
 /home/charlie/Desktop/libc6_2.3.5-8.1_i386.deb
root@ubuntu:/home/charlie #

and story goes go on and on and on, every time i am asked to install anodher package, it seems to me that i need to reinstall whole ubuntu:confused: 

what i doing wrong????

---

### Post by lisje on 2005-12-02
I think it is the best thing that you try to install ubuntu again.. maybe something went wrong.
At least that is what I do when something that would normally install properly, refuses.

In an fresh ubuntu install I usually use these commands:
```
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
sudo update-alternatives --config java
```

I'm not at my ubuntubox so I fetched the commands from another post.
I use the software development package from sun... not the runtime environment.

those commands have always worked for me. Java is the one thing I never had trouble with.
I don't know if it helps.
Greets,
Lisje

---

### Post by vvnoob on 2005-12-02
[QUOTE=lisje]
In an fresh ubuntu install I usually use these commands:
```
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb
sudo update-alternatives --config java
```

Lisje[/QUOTE]

after first command i get this>

charlie@ubuntu:~$ sudo apt-get install fakeroot java-package java-common
Password:
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
java-package is already the newest version.
java-common is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libasound2: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to be inst alled
  libasound2-dev: Depends: libasound2 (= 1.0.8-1) but 1.0.10-1 is to be installe d
  libasound2-plugins: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to  be installed
                      Depends: libjack0.100.0-0 (>= 0.100.0) but it is not insta llable
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-22) but 2.3.2.ds1-20ubuntu14 is to be i nstalled
  libjack0.100.0-dev: Depends: libjack0.100.0-0 (= 0.100.0-4) but it is not inst allable
  libswt-gtk-3.1-java: Depends: libswt-gtk-3.1-jni (= 3.1-3) but it is not going  to be installed
W: Couldn't stat source package list [http://packages.debian.org](http://packages.debian.org) hoary/multiverse  Packages (/var/lib/apt/lists/packages.debian.org_ubuntu_dists_hoary_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
charlie@ubuntu:~$

so systems see newest jawa BUT :

root@ubuntu:/home/charlie # dpkg -i /home/charlie/Desktop/azureus_2.2.0.2-1_i386.deb
Selecting previously deselected package azureus.
(Reading database ... 68230 files and directories currently installed.)
Unpacking azureus (from .../azureus_2.2.0.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of azureus:
 azureus depends on sun-j2sdk1.5 | java2-runtime; however:
  Package sun-j2sdk1.5 is not installed.
  Package java2-runtime is not installed.
dpkg: error processing azureus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 azureus

:confused: 

TNX for ur help. But i really dont want to reinstall Hoary its working fine 4 me exept this java problem.

Is next dist of ubuntu 5.10 simply upgradabe? I think in windows way: upgrade for example from win98 to winXP. Ubuntu is only OS i have i dont have Win... on second particion and i dont want to lose documents and settings from me Hoary...


regrets

---

### Post by lisje on 2005-12-02
[QUOTE=vvnoob]
Is next dist of ubuntu 5.10 simply upgradabe? I think in windows way: upgrade for example from win98 to winXP. Ubuntu is only OS i have i dont have Win... on second particion and i dont want to lose documents and settings from me Hoary...
regrets[/QUOTE]

A lot of people seem to have succeeded in simply upgrading. I did not try that. Because you're upgrading from gcc 3.3.4 to gcc 4.0 which is a big step.
Someone told me that it is a risk because programs compiled with gcc 3.3.4 are likely to cause problems in an environment that uses gcc 4.0.

But many people seem to have successfully upgraded from hoary to breezy by just changing their "sources.lst".
you could probably try it. Perhaps you problems will be solved.

Greets,
Lisje

---

