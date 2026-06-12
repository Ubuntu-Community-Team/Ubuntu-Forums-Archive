---
title: "How to install programs (VLC, java) without internet"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by cdiem on 2007-04-22
Hi, I'm pretty new in this great operating system (about 2 months with Edgy). All of a sudden, a week ago my ISP locked my MAC address, so now I cannot access the internet via the computer with Ubuntu on it. And several days ago I installed ubuntu feisty, without being able to downlaod anything from the internet.

My question is, is there a way to install the following applications:
1. VLC (for media, cause it doesn't need codecs)
2. JRE (as I use a translations tool OmegaT, which runs under java)
3. gbgoffice (dictionary, as my native language is bulgarian)

I tried to compile them (have installed build-essential from the CD image of Feisty), but it looks like they need some dependencies, and their dependencies need other dependencies and so on, until I cannot trace them.
Is there a package, with all the dependancies in it, something like a big .deb file?

I'll appreciate any help and opinions, that you'd post.
Thanks in advance!

---

### Post by Malta paul on 2007-04-22
Hi welcome,
I would say you need a internet connection to get VLC etc.
One way would be take your live disk to a friends computer that is connected to the internet. Then down load the packages to a USB pen drive. ( the live dsk is read only) 
Hope this helps  :)

---

### Post by xyz on 2007-04-22
[CHECK THIS OUT]("http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/")
Good luck.

---

### Post by cdiem on 2007-04-22
Thanks. I actually have windows xp on my other computer, which is connected to the internet; I have downlaoded the files on my USB drive and tried to install them, but as I said, without internet it's far too complicated to install even a single utility (say, vlc for instance). I searched for a .deb file ot this player via Google, but all i could find was vlc.0.4 or something, which is far too old, and I'm frankly afraid to install this on my computer. If you know of a .deb file (ot tar.gz file, comprising all the dependancies in it) it'd be great. Actually, when I tried to ./configure vlc, it could not find some header file; the gbg office depends on libsig++2, gtkmm-2.4 and glibmm-2.4. Of them i managed to compile just one of the libraries, adn then it said I needed glibc 2.0. So i tried to compile glib from source and it said i need another 3 dependancies - and i simply gave it up, cause i didn't want to download everything from the internet and compile it, just to check whether it works,or it would ask me for more dependencies. But, if there's really some file, that would work, no matter how, I'd love to use it. I could not find one.

---

### Post by cdiem on 2007-04-22
I cannot express my thankfulness, XYZ! Thanks a lot! I saw your post right now - I think that's just what I needed. 
The only problem is, that my other computer runs under windows. But i'll try to boot it with a livecd and then run wget. The script on that site is lifesaving. Thanks one more time.

---

### Post by xyz on 2007-04-22
No problem!
Come back and let us know how it went!!

---

### Post by Malta paul on 2007-04-22
Great news, Have fun :guitar:

---

### Post by nazish on 2007-04-22
spoofing MAC address is not a big deal in linux

all you need to do is run these three commands

this command stops the network

1. sudo ifconfig eth0 down


2. sudo ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx

where xx ...xx is the mac address of your windows machine
running this command changes or spoofs your original mac address to that of windows

then start the network

3. sudo ifconfig eth0 up

after this change the IP address of your UBUNTU machine to that of windows. Viola you have your Ubuntu PC ready to be connected to the net.

bye

regards,
naz.

---

### Post by cdiem on 2007-04-22
to nazish >> Thanks, i tried this, but it keeps giving me "invalid ether address", probably i don't do something right - but this is a nice trick, anyway. 
I did not know this before. Btw., does this mean, that one with a linux can obtain any mac address - say, if I want to go to the internet club with my laptop and ask them, and then connect my laptop to the lan cable of their computer, this would give me access to internet, even though they have a mask on the addresses there? Cause i tried also this one, (but without knowing your tip), and without result.

to xyz >> by your great address, i found this great tool apt-medium, [http://wiki.debian.org/AptMedium](http://wiki.debian.org/AptMedium). Now I'm struggling to change from drive C:\ to drive J:\ in windows :) (cannot with cd j:\, but I will keep trying anyway:)  ) which is where my usb disk is in. When I manage, I'll post results :)

---

### Post by nazish on 2007-04-23
sorry for being late cdiem,
this  works fine for my system. yes with this method you can connect your Linux machine to the internet the only thing that is required is that you need the  mac address of the other machine which you want to fake, then change the IP address of your machine, then your machine will be identified as the original machine whose mac and IP you are using, think I made it clear. Please let me know if you still are having any trouble.
bye
regards,
naz.

---

### Post by cdiem on 2007-04-23
Well, ok, I ran 
sudo apt-get -qq --print-uris update |awk -F\' '{print $2} >get.lst
following the instructions at [http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)
and then copied the file get.lst to another machine, with internet.

The file was: 

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-bg.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-bg.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-bg.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-bg.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-bg.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-bg.bz2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-bg.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-bg.bz2)
[http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-bg.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-bg.bz2)
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.bz2
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.bz2
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/Release.gpg
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/i18n/Translation-bg.bz2
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/i18n/Translation-bg.bz2

Then I ran wget, and got 3 packages, one named Release.qpq  and two named Sources.bz2 and Packages .bz2

To me it's a little bit strange, since I don't know how to add the qpq to the machine with ubuntu (without internet). I feel I'm close to updating, so that later I could install some apps too (cause right now I cannot see them in synaptic); but still I need some help.

Please, how do I add these 3 files, and update my sistem?

---

