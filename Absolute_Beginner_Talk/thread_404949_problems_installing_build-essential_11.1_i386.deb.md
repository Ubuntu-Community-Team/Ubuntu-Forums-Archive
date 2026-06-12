---
title: "problems installing build-essential_11.1_i386.deb"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Dj Delta9 on 2007-04-09
Hello all.  This is just one small problem of a much larger problem, but if we figure this out the rest might fall into place so we'll start with this.  I've searched many threads and can't seem to figure this out, so here it is...
  
I'm running dapper, with no internet connection, trying to install build-essential_11.1_i386.deb with the package installer.  I have another box running XP and a USB drive so I can download whatever I need and transfer it.

So I double click on the package and I get an information box that says "Same version is available in a software channel."  I assume that means it's on the Ubuntu disk I have in my cd drive, but I really don't know.  

So I click close and then Install Package.  Now it says it's downloading additional packages and it activates my cd, but does not download anything and exits the package installer without installing build-essential.  

The 4 additional packages it tries to download are:  
libc6-dev
g++-4.0
libstdc++6-4.0-dev
g++

So I download all of those through XP and transfer via USB drive.

Each one of these requires the other 3 to be installed at the same time, in which case the Package Installer tries to download them, fails, and exits without installing anything.

The only one that doesn't do this is libc6-dev_2.3.6-0ubuntu20_i386.deb...It just gives the following message:

Error: Dependency is not satisfiable: libc6

And thats where I am.  Can anyone help this cranky noob?  I hope so.
:confused:

---

### Post by meborc on 2007-04-09
since you have internet on your other box, can't you just connect your dapper to internet? ... or is there hardware problems? no internet-card?

sorry for not helping much :D

---

### Post by zvacet on 2007-04-09
"Same version is available in a software channel."This massage means that you can install that package with synaptic or apt-get.That means nothing to you because you don´t have net.About package.You need to download package and all dependencies(mark with red ball),and when you do that installation will be easy. I belive you downloaded package from this site
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by Dj Delta9 on 2007-04-09
:cool: No worries, I didn't mention this becuase I didn't want to seem like I was hijacking, but since you asked...  I just finished setting up a wireless network, linksys WRT54G router, and linksys WMP54G NIC, on the XP box.  So I'm trying to get a dell 1450 wireless USB adapter to work under Ubuntu, which is the main problem to this smaller side problem that I'm having.

---

### Post by Dj Delta9 on 2007-04-09
That is where I was downloading from so I will give what you said a shot..

---

### Post by Dj Delta9 on 2007-04-09
Ok.  So I downloaded all the build-essential dependency packages, which are basically the packages I downloaded in the first place (orginal post)  plus some packages that are already installed.  So I'm back to where I started.  I need to find a way to install the packages one by one, but package installer will not let me do that.  Is there any way I can install them in terminal?  Or any other ideas?

---

### Post by Bachstelze on 2007-04-09
build-essential iis on your Ubuntu CD, no need to bother with all the dependencies, just do :
```

sudo apt-cdrom add
*insert Ubuntu CD here and press Enter*
sudo aptitude update
sudo aptitude install build-essental
```

---

### Post by Dj Delta9 on 2007-04-09
So I followed the instructions up to this next part and got the following

> djdelta9@the-matrix:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
   g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
The following packages have been kept back:
   evolution evolution-data-server evolution-plugins file firefox
   firefox-gnome-support kdelibs-bin kdelibs-data kdelibs4c2a
   language-pack-gnome-en libaudio2 libcamel1.2-8 libebook1.2-5 libecal1.2-3
   libedata-book1.2-2 libedata-call.2-1 libedataserver1.2-7
   libedataserverui1.2-6 libegroupwise1.2-9 libexchange-storage1.2-1
   libfreetype6 libkrb53 ligmagic1 libmysqlclient15off libnspr4 libnss3
   libwpd8c2a libxfont1 libxine-main1 mysql-common openoffice.org
   openoffice.org-base openoffice.org-calc openoffice.org-common
   openoffice.org-core openoffice.org-draw openoffice.org-evolution
   openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
   openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
   openoffice.org-writer python-uno ttf-opensymbol xmms xserver-xorg-core
The following NEW packages will be installed:
   build-essential g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
0 packages upgraded, 5 newly installed, 0 to remove and 48 not upgraded
need to get 2822kb/6527kb of archives.  After unpacking 25.5MB will be used.
Do you want to continue?  [Y/n/?] y
Writing extended state information... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libc6-dev 2.3.6-0ubuntu20.4
   Temporary failure resolving 'us.archive.ubuntu.com'
djdelta9@the-matrix:~$

So I assume that it's still not installed...](*,)
anymore suggestions?

---

### Post by Dj Delta9 on 2007-04-13
Nevermind.  I decided to just do a clean install and move the box to where I could use my ethernet connection.  thanks for the suggestions though! :guitar:

---

