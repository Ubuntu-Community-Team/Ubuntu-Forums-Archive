---
title: "No experience in gcc, need to compile programs"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-05-25
I used to do my programming exercises in Borland C under Windows but now that I have Ubuntu I don't know how to handle gcc. I have it installed but the #include<iostream.h> (same with stdio.h, conio.h) gives an error message "file not found." I have no idea where the *.h files are stored to include them, or if I have to download and place them somewhere. I know the basics of C++ but I can't manage the compiler yet. Any suggestions/links will be appreciated.

---

### Post by lazyart on 2007-05-25
did you```
sudo apt-get install build-essential
```

---

### Post by kevdog on 2007-05-25
Hey another thing you might try -- ran into this problem myself about 2 weeks back (as a new g++ user)

Do the following (for c++) if you are trying to go it this way!

```

#include <iostream>

using namespace std;

int main (void){

   cout<<"Hello World!"<<endl;

   return 0;
}


```

The using namespace std is key!

---

### Post by NT4.0 on 2007-05-25
lazyart, I looked through build-essential dependencies and found that the *.h files were in the libc6-dev_2.3.6-0ubuntu20_i386 package. However, I can't install it. When I open the package and try to install it with Gdebi, I get the error "Dependency is not satisfiable: libc6". Forcing the package in Synaptic didn't help either. Should I extract the *.h files and copy them in /usr/include manually?? I updated the database of Synaptic packages, but no luck. Synaptic error: "libc6-dev: Depends: libc6 (=2.3.6-0ubuntu20.4) but 2.4-1ubuntu6 is to be installed". By the way, build-essential does not seem to be necessary for simple programming exercises... or does it?

kevdog, I'll take your advice as soon as I finally get gcc functional :)

---

### Post by kevdog on 2007-05-25
At the command line what happens when you just type:

sudo aptitude install build-essential

Im going to be honest with you.  I just starting using gcc a couple of weeks ago on Ubunutu, and I dont specifically remember installing this package.  It might have been installed by default.

If I do a sudo aptitude search build-essential
this is the following output:

p build-essential  --inormational list of build-essential packages

I dont know what the "p" means.  Packages that are installed usually come back with a i rather the p.  Maybe someone else can help here.

---

### Post by NT4.0 on 2007-05-26
kevdog,

Here is the output of "sudo aptitude install build-essential":

<out>
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
The following NEW packages will be automatically installed:
  g++ g++-4.0 libstdc++6-4.0-dev
The following packages have been kept back:
  acpi-support app-install-data app-install-data-commercial base-files
  bind9-host binutils-static capplets-data cpio cupsys cupsys-bsd
  cupsys-client dbus dbus-1-utils deskbar-applet desktop-file-utils
  dnsutils dpkg dselect ekiga eog evince evolution evolution-data-server
  evolution-plugins file file-roller firefox firefox-gnome-support gdb gdm
  gedit gedit-common gimp gimp-data gimp-python gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-desktop-data
  gnome-doc-utils gnome-games gnome-games-data gnome-media gnome-menus
  gnome-panel gnome-panel-data gnome-screensaver gnome-session
  gnome-terminal gnome-terminal-data gnome-themes gnupg gstreamer0.10-alsa
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.8 gzip hal hal-device-manager info language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libbind9-0
  libcamel1.2-8 libcupsimage2 libcupsys2 libdbus-1-2 libdbus-glib-1-2
  libdns21 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data
  libegroupwise1.2-9 libexchange-storage1.2-1 libfreetype6 libgd2-noxpm
  libgeoip1 libgimp2.0 libglib2.0-0 libglib2.0-data libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnutls12 libgsf-1-113
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml3.8-15 libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-7 libhal-storage1 libhal1 libisc11
  libisccc0 libisccfg1 libkrb53 liblwres9 libmagic1 libmagick9 libmetacity0
  libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3
  libnautilus-extension1 libnspr4 libnss3 libpanel-applet2-0 libpng12-0
  libpoppler1 libpoppler1-glib libpq4 libqt3-mt librpm4 libsmbclient
  libsnmp-base libsnmp9 libsoup2.2-8 libspeex1 libssl0.9.8 libtiff4
  libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common
  libwnck18 libwpd8c2a libx11-6 libxfont1 linux-386 linux-image-386
  linux-restricted-modules-386 linux-restricted-modules-common locales
  login lvm2 mc metacity mozilla-thunderbird mysql-client-5.0 mysql-common
  mysql-server mysql-server-5.0 nautilus nautilus-cd-burner nautilus-data
  openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  openssh-client openssl passwd pcmcia-cs pmount poppler-utils ppp
  python-gmenu python-pyorbit python-uno python-vte python2.4
  python2.4-dbus python2.4-examples python2.4-gdbm python2.4-minimal
  python2.4-pyorbit python2.4-tk rdesktop rpm samba-common screen slocate
  smbclient sound-juicer ssh-askpass-gnome synaptic tar tcpdump
  ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-standard w3m
  wpasupplicant xinit xmms xorg-driver-fglrx xserver-xorg-core
  xserver-xorg-input-mouse yelp zenity
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev
0 packages upgraded, 5 newly installed, 0 to remove and 243 not upgraded.
Need to get 2822kB/6572kB of archives. After unpacking 25.5MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.4-1ubuntu6 is installed.Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
xmms-wma

Upgrade the following packages:
mc [4.6.0-3 (now) -> 1:4.6.1-1ubuntu2 (dapper)]

Downgrade the following packages:
libc6 [2.4-1ubuntu6 (now) -> 2.3.6-0ubuntu20.4 (dapper-updates)]

Score is -437

Accept this solution? [Y/n/q/?]
</out>

I don't understand why it wants to install g++ when I already have gcc. Is g++ a new standard and gcc a deprecated one? And it wants to remove xmms-wma what will make me unable to play wma files (to hell with them, still I have quite a number of them :) ). Besides, I have no idea why the libc6 package needs to be downgraded and what mc has to do with it. I will stick to this solution if nothing else can be done, but for now I canceled it and have been waiting for some more recommendations.

---

### Post by kevdog on 2007-05-26
There is something wrong with your libc6-dev package as it states it is broken.  Sometimes I have been presented options like this with a score at the bottom.  Although I use aptitude about 99% of the time, try using Synaptice and either removing and then reinstalling the libc6-dev package.  Sorry I dont have to much input.  I dont know what is exactly going on.

---

### Post by taurus on 2007-05-26
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by kevdog on 2007-05-26
What version of ubuntu are you using??  Im using Fesity with libc6-dev version 2.5-0ubuntu14 installed.

---

### Post by taurus on 2007-05-26
> **kevdog said:**
> What version of ubuntu are you using??  Im using Fesity with libc6-dev version 2.5-0ubuntu14 installed.

I suppose Dapper, from his profile.

---

### Post by NT4.0 on 2007-05-26
First of all I need to tell you guys that I have dial-up (56K modem) and something that's bigger than 5M to download makes things hard. Due to this fact I have to download big packages by hand somewhere with broadband access and install them manually or through "Add downloaded packages" option in Synaptic.

So I checked the dependencies for build-essential in the first place, downloaded and tried to install libc6-dev only to find it was incompatible with libc6. I messed around with libc6-dev for a while in Synaptic, tried to "Force package" but couldn't figure out where the problem was.

In Synaptic libc6 is marked as "not installed".

kevdog, I use Ubuntu 6.06 LTS and plan on using it further.

taurus, here it is:

<out>
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
</out>

---

### Post by taurus on 2007-05-26
You know that build-essential is on the CD and since you already have an entry for the CD, insert it into a drive and run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by NT4.0 on 2007-05-27
taurus,

I did like you said and it took some 30 minutes but the packages downloaded and I resolved another problem that has kept me annoyed for the whole year since I switched to Linux. In the command line mode (no X) mc looked like in the screenshot attached, all other text apps had a similar look so I could work with them only in Gnome terminal. After I downgraded libc6 mc was like this in Gnome but after I rebooted the problem disappeared altogether. Great!

I am checking out gcc.

---

### Post by KIAaze on 2007-05-27
_1)Things you should know:_
> I don't understand why it wants to install g++ when I already have gcc. Is g++ a new standard and gcc a deprecated one? 


gcc is used to compile C code and g++ is used to compile C++ code. That's all.

"build-essential" is a package that contains all essential programs, headers, libraries, etc... necessary for the compilation of basic C/C++ programs.
It allows you to install from source (from the tar.gz files you can find on the web).

_2)Some tips for when your gcc/g++ problems are solved:_
Now once you'll have solved your installation problem of gcc and g++ (g++ is to compile C++ code by the way) and are able to compile the hello world program by doing "gcc -o hello hello.c" or "g++ -o hello hello.cpp", you might also want to try the different GUIs available for GNU/Linux, i.e the equivalents of Borland C++. ;)

Here are some IDEs (Integrated Development Environment) for GNU/Linux:
-[Anjuta]("http://anjuta.sourceforge.net/") (Only one I really used until now. Very practical to create GTK apps with Glade. :) )
-[Code::Blocks]("http://www.codeblocks.org/") (cross-platform)
-[KDevelop]("http://www.kdevelop.org/") (has an RPM creation feature, but I have been unable to find a .deb creation feature :( )
-[Eclipse]("http://www.eclipse.org/") (java-based, so it might be slow, and i's also more java oriented. I never really managed to compile something with it... Seems bloated and complex. A lot of people say it's great howvever. :/)

See also:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")

Most, if not all, IDE under GNU/Linux automatically create a Makefile for your program. :D
(The Makefile is what allows you to compile a program by typing "make" in a console.)

[Under Windows there is also [DevC++]("http://www.bloodshed.net/devcpp.html") if you are looking for a free one instead of the proprietary Borland C++.
Code::Blocks also works under Windows.]

---

### Post by NT4.0 on 2007-05-27
KIAaze, thanks!! g++ hello.cpp -o hello.out works!

By the way, when I downgraded libc6, xmms stopped working right (the playlist/equalizer windows get stuck on screen and can't be moved). I'm going to switch to vlc anyway, it seems to be way more powerful.

Great to know I can now compile programs from source! Is it safe (I mean possible conflicts with the pre-packaged software installed through Synaptic)?

It is interesting that Synaptic does not show these conflicts. The xmms status there is "installed" but when I open the xmms deb package in gdebi, it says "conflicts with installed package 'xmms'" and the install button is disabled. I wonder if some more programs will soon turn up dysfunctional.

I will check out Anjuta.

---

### Post by KIAaze on 2007-05-27
Yes, installing from source can cause conflicts.

Whenever possible, install through synaptic (or add/remove programs)(or apt-get since that's the same only in command-line).
Anjuta for example, is availbale in synaptic. ;)

You should only install from source if there is no better solution.

So here's a little installation order:
1)Install through synaptic/apt-get
2)Install .deb package
3)Install from source

There are of course also other installation possibilities like installing an RPM package through "alien" or using other package managers, but I don't know enough about them to tell you how "safe" they are.

---

