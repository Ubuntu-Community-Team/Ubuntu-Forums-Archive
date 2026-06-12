---
title: "Upgraded from 7.04 to 7.10 -- well almost -- need help please !"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-10-16
Just tried to upgrade from 7.04 to 7.10 and most everything went ok until the end when I kept getting errors for dependencies out the ying yang! Tried to re- install one of the programs via "sudo aptitude install util-linux"  and  got this in terminal


jerrynewt@Jerry2:~$ sudo aptitude install util-linux
[sudo] password for jerrynewt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libatk1-ruby libavahi-compat-howl0 libavcodec0d libavformat0d 
  libcairo-ruby libcrypto++5.2c2a libflac++5c2 libgdk-pixbuf2-ruby 
  libglib2-ruby libipod-cil libipodui-cil libjack0.100.0-0 libntfs-3g0 
  libpango1-ruby libportaudio2 libpostproc0d libquicktime0 librte1 
  libswfdec0.3 libwxgtk2.4-1 python-qt3 python-sip4 
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a 
The following partially installed packages will be configured:
  language-pack-en language-pack-en-base language-pack-gnome-en 
  language-pack-gnome-en-base locales sun-java5-bin sun-java5-jre 
  sun-java6-bin sun-java6-jre sun-java6-plugin tzdata ubuntu-minimal 
  util-linux util-linux-locales 
0 packages upgraded, 0 newly installed, 22 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 41.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 locales
 language-pack-en-base
 sun-java5-jre
 util-linux
 ubuntu-minimal
 language-pack-en
 language-pack-gnome-en-base
 sun-java6-jre
 sun-java5-bin
 util-linux-locales
 language-pack-gnome-en
 sun-java6-bin
 sun-java6-plugin
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done 

Any ideas what I did wrong or what I need to do to fix these problems ?? I have 7.10 installed on a dual boot at home with 7.04 and it works flawlessly -- Compiz - Fusion is amazing !! This is my laptop (Toshiba Satellite Pro -- 40Gig HD -- Pent 4 Processor) with 7.04 and Windows dual boot. Any help with this would be really appreciated. Thanks for the time.

---

### Post by Whiffle on 2007-10-16
try

'apt-get -f install'  

I'm upgrading to gutsy on my desktop right now and the upgrader died.  So i'm doing it manually...

oh and you'll want to do apt-get upgrade after that

---

