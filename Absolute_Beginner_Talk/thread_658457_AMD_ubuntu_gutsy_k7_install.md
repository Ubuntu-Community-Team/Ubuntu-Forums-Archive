---
title: "AMD ubuntu gutsy k7 install?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by fenixfox on 2008-01-04
here is what i have tried. I looked a several other posts and have tried the following:

root@trishaandbrian-desktop:~# sudo cat /proc/sys/vm/swappiness
10
root@trishaandbrian-desktop:~# vm.swappiness=10 to /etc/sysctl.conf
bash: vm.swappiness=10: command not found
root@trishaandbrian-desktop:~# /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied
root@trishaandbrian-desktop:~# etc/inittab
bash: etc/inittab: No such file or directory
root@trishaandbrian-desktop:~# edit /etc/inittab
Warning: unknown mime-type for "/etc/inittab" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
root@trishaandbrian-desktop:~# ooffice -quickstart &
[1] 6960
root@trishaandbrian-desktop:~# apt-get install bum
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  adept-common libept0 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtk2-gladexml-perl
The following NEW packages will be installed:
  bum libgtk2-gladexml-perl
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 129kB of archives.
After unpacking 770kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe libgtk2-gladexml-perl 1.006-1 [45.1kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe bum 2.1.10-1 [84.0kB]
Fetched 129kB in 0s (130kB/s)           
Selecting previously deselected package libgtk2-gladexml-perl.
(Reading database ... 114757 files and directories currently installed.)
Unpacking libgtk2-gladexml-perl (from .../libgtk2-gladexml-perl_1.006-1_i386.deb) ...
Selecting previously deselected package bum.
Unpacking bum (from .../archives/bum_2.1.10-1_all.deb) ...
Setting up libgtk2-gladexml-perl (1.006-1) ...
Setting up bum (2.1.10-1) ...

[1]+  Done                    ooffice -quickstart
root@trishaandbrian-desktop:~# sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Get:4 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                      
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources             
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 4B in 0s (4B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@trishaandbrian-desktop:~# sudo apt-get build-dep linux-image-2.6.10-5-k7
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@trishaandbrian-desktop:~#  sudo apt-get build-dep linux-image-2.6.10-5-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux-image-2.6.10-5-k7
root@trishaandbrian-desktop:~# sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  adept-common libept0 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/111kB of archives.
After unpacking 442kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Selecting previously deselected package fakeroot.
(Reading database ... 114831 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Setting up fakeroot (1.7.1ubuntu1) ...

root@trishaandbrian-desktop:~# sudo apt-get install devscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  adept-common libept0 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev patch
Suggested packages:
  devscripts-el build-essential cvs-buildpackage cvs subversion svk tla bzr
  git mercurial debian-keyring dupload dput gnuplot libcrypt-ssleay-perl
  libsoap-lite-perl libtimedate-perl lintian linda mailx mailutils mutt
  patchutils ssh wdiff diff-doc
The following NEW packages will be installed:
  devscripts dpkg-dev patch
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 394kB/652kB of archives.
After unpacking 2118kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main devscripts 2.10.7ubuntu5 [394kB]
Fetched 394kB in 3s (105kB/s)      
Selecting previously deselected package patch.
(Reading database ... 114870 files and directories currently installed.)
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package devscripts.
Unpacking devscripts (from .../devscripts_2.10.7ubuntu5_i386.deb) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up devscripts (2.10.7ubuntu5) ...

root@trishaandbrian-desktop:~# apt-get source linux-image-2.6.10-5-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux-image-2.6.10-5-k7
root@trishaandbrian-desktop:~# cd linux-image-2.6.10-5-k7
bash: cd: linux-image-2.6.10-5-k7: No such file or directory
root@trishaandbrian-desktop:~# sudo gedit linux-image-2.6.10-5-k7
root@trishaandbrian-desktop:~# apt-get install linux-image-2.6.10-5-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.10-5-k7
root@trishaandbrian-desktop:~# apt-get install linux-k-2.6.10-5-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-k-2.6.10-5-k7
root@trishaandbrian-desktop:~# sudo apt-get install linux-k7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-k7
root@trishaandbrian-desktop:~# 

what am i doing wrong? I have went to synaptic and did a search for linux-image-2.6.10-5-k7 which I read on this site: [http://www.linuxjournal.com/article/8322](http://www.linuxjournal.com/article/8322)
I use an AMD 3200 
I am trying to install this to increase performance if there is a better one I need I would love to know. Thanks again in advance!

---

### Post by fenixfox on 2008-01-04
bump

---

### Post by plucky on 2008-01-04
Fenixfox,

Why are you trying to downgrade your kernel?

The article you linked to was from 2005,and there is no need to build a special kernel for AMD K7 processors anymore.If you search the Gutsy repositories for **linux-image** you wont find that image as it is now outdated.

Plucky

---

### Post by dcstar on 2008-01-05
> **plucky said:**
> 
........
The article you linked to was from 2005,and there is no need to build a special kernel for AMD K7 processors anymore.If you search the Gutsy repositories for **linux-image** you wont find that image as it is now outdated.


Exactly, you can recompile the current kernel with the AMD option enabled, but the performance "benefit" is so marginal over the generic kernel that all the trouble that you will have to go through is hardly worthwhile.

The only worthwhile AMD upgrade these days is to go to the 64bit Ubuntu (if your system supports it......)      ;)

---

