---
title: "[SOLVED] Help Apt-get error"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by lagooned on 2007-11-08
Hello im running ubuntu 7.04 (upgraded from 6.10 if that helps at all)

i was looking on this forum like 15 min ago when i found a app 4 costimising compiz, i never 

had tried compiz so i installed the app gnome-compiz-manager

so one i installed it i opened it up i found that compiz didnt work. i thought that this was due to my version of compiz so i installed compiz again.
i said

$ sudo apt-get install compiz

then it said something like:

The following packages will be upgraded:
compiz-gnome
The following packages will be replaced:
compiz-gtk

Are you sure you want to do this Y/n (or something like that):

me being new to apt-get, i said yes

then when i it got done i tried to install another compiz costimation app.
i got this:

E: Sub-process /usr/bin/dpkg returned an error code (1)

i got worried and tried to reinstall compiz-gtk
and when i did i got this:

sudo apt-get install compiz-gtk

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
compiz: Depends: compiz-decorator
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

i've tried everything, done exactly what is said:

$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libgnucrypto-java sdljump-data liquidwar-server libglitz-glx1 libcvsservice0
lincity-ng-data libnl1-pre6 librdf0 network-manager libwww-ssl0 libkjsembed1
libsdl-gfx1.2-4 trigger-data libnm-util0 libzvbi0 kdevelop-data libpcap0.7
python-pyogg gftp-common libsqlite0 xmame-common libdv-bin snes9x-x
gdk-imlib1 mencoder librasqal0 libseda-java libcommons-cli-java libgtk-jni
libsnack2 python-pyvorbis kdesvn-kio-plugins libalut0 libcairo-java dhcdbd
librpcsecgss2 python-mutagen cvs libbcprov-java libzvbi-common libxine-main1
libglitz1 libglib-java neverdata kamefu-data python-wxversion libsvnqt3
libkamefu0 libgtk-java python-wxgtk2.6 openvpn libzvt2 xmame-sdl
liballegro4.2 tuxkart-data liquidwar-data
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1376kB of additional disk space will be used.
(Reading database ... 163724 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

And then i tried:

$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
libgnucrypto-java sdljump-data liquidwar-server libglitz-glx1 libcvsservice0
lincity-ng-data libnl1-pre6 librdf0 network-manager libwww-ssl0 libkjsembed1
libsdl-gfx1.2-4 trigger-data libnm-util0 libzvbi0 kdevelop-data libpcap0.7
python-pyogg gftp-common libsqlite0 xmame-common libdv-bin snes9x-x
gdk-imlib1 mencoder librasqal0 libseda-java libcommons-cli-java libgtk-jni
libsnack2 python-pyvorbis kdesvn-kio-plugins libalut0 libcairo-java dhcdbd
librpcsecgss2 python-mutagen cvs libbcprov-java libzvbi-common libxine-main1
libglitz1 libglib-java neverdata kamefu-data python-wxversion libsvnqt3
libkamefu0 libgtk-java python-wxgtk2.6 openvpn libzvt2 xmame-sdl
liballegro4.2 tuxkart-data liquidwar-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
compiz-gnome
The following packages will be upgraded:
compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1376kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163724 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please if you can help me, it wont let me install apps! and Installing applications is pretty much all i like to do. And compiz is not that important to me, so if i have to uninstall it, its ok, i just wanted to try it, thank you for reading.

---

### Post by TadH on 2007-11-08
im pretty newe to but i think you need to run beryl on 7.04, i might be mistaken but compiz/fusion is for 7.10 do you have beryl?>

---

### Post by lagooned on 2007-11-08
not compiz-fusion just normal compiz

---

### Post by Maestro23 on 2007-11-08
Goto /var/cache/apt/archives/

look for compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb

and try deleting it.

> cd /var/cache/apt/archives

ls (lists files)

If any compiz package is there try

sudo dpkg -P packagename
or
sudo dpkg -P compiz*

Then run

> sudo apt-get update

sudo apt-get upgrade

---

### Post by bks on 2007-11-08
You could also try using Synaptic to search for and remove Compiz, then reinstalling. Synaptic will help resolve dependencies. You can use Add/Remove in the Applications menu to download a GUI for configuring compiz too.

Alternatively use:
```

sudo aptitude install ccsm

```

---

### Post by lagooned on 2007-11-08
I did that and i got this:

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jared@*****-desktop:/var/cache/apt/archives$ sudo dpkg -P compiz-gnome dpkg: dependency problems prevent removal of compiz-gnome:
 gnome-compiz-manager depends on compiz-gnome; however:
  Package compiz-gnome is to be removed.
dpkg: error processing compiz-gnome (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 compiz-gnome

it seems as though that the program that i installed first depends on compiz-gnome so to i have to remove that?

---

### Post by lagooned on 2007-11-08
ok i removed the package Gnome-compiz-manager or something, but when i try to remove a random app this happens:

> jared@*****-desktop:/var/cache/apt/archives$ sudo apt-get remove kino (sorry if you like kino)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


then i try to install compiz-decorator an it points to two packages:

> jared@*****-desktop:/var/cache/apt/archives$ sudo apt-get install compiz-decorator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-decorator is a virtual package provided by:
  compiz-kde 1:0.5.5~git20071006+3v1ubuntu0
  compiz-gnome 1:0.5.5~git20071006+3v1ubuntu0
You should explicitly select one to install.
E: Package compiz-decorator has no installation candidate

 And the whole thing starts over again! so i choose to install compiz gnome and this happens:

> jared@*****-desktop:/var/cache/apt/archives$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libgnome-compiz-manager0 sdljump-data liquidwar-server
  libglitz-glx1 libcvsservice0 lincity-ng-data libnl1-pre6 librdf0
  network-manager libwww-ssl0 libkjsembed1 libsdl-gfx1.2-4 trigger-data
  libnm-util0 libzvbi0 kdevelop-data libpcap0.7 python-pyogg gftp-common
  libsqlite0 xmame-common libdv-bin snes9x-x gdk-imlib1 mencoder librasqal0
  libseda-java libcommons-cli-java libgtk-jni libsnack2 python-pyvorbis
  kdesvn-kio-plugins libalut0 libcairo-java dhcdbd librpcsecgss2
  python-mutagen cvs libbcprov-java libzvbi-common libxine-main1 libglitz1
  libglib-java neverdata kamefu-data python-wxversion libsvnqt3 libkamefu0
  libgtk-java python-wxgtk2.6 openvpn libzvt2 xmame-sdl liballegro4.2
  tuxkart-data liquidwar-data
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  compiz-gnome
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 1487kB of additional disk space will be used.
(Reading database ... 163665 files and directories currently installed.)
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20071006+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by lagooned on 2007-11-08
OH... God im embarissed, i figured it out!
See what was wrong is when i updated my compiz that version was from the Avant Windows Navigator repositoy (kinda wierd Huh?)

so what i had to do was go into the synaptic package manager, select the current version of compiz (it was broken) select force version and then select the other version.

thanks for all your help!

---

### Post by Maestro23 on 2007-11-08
> **lagooned said:**
> OH... God im embarissed, i figured it out!
See what was wrong is when i updated my compiz that version was from the Avant Windows Navigator repositoy (kinda wierd Huh?)

so what i had to do was go into the synaptic package manager, select the current version of compiz (it was broken) select force version and then select the other version.

thanks for all your help!

Good deal man. Please mark this SOLVED using the Thread Tools.

Thanks.:guitar:

---

