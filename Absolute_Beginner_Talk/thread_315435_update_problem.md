---
title: "update problem"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-09
hi i am try several update with command 
sudo apt-get install ---------

then i get a error - 

xxxxxx@root-desktop:~$ sudo apt-get install ------
Reading package lists... Error!
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
E: Dynamic MMap ran out of room
E: Error occurred while processing vde (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
lakhan@root-desktop:~$ sudo apt-get install xpad
Reading package lists... Error!
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
E: Dynamic MMap ran out of room
E: Error occurred while processing vde (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.



what i do:( :( :(

---

### Post by ajgreeny on 2006-12-09
I think your problem is that you have both edgy and dapper repos showing in your errors, so presumably in your sources.list file as well.  Depending on your version of ubuntu delete the repos in sources.list that are for the wrong version and try updating again.

---

### Post by lucky_chouhan on 2006-12-09
what i do ](*,) ](*,) ](*,)

---

### Post by tchoklat on 2006-12-09
you need to edit your sources list and (assuming you are using edgy) delete all the lines with dapper in them.

---

### Post by lucky_chouhan on 2006-12-09
after delete my file look like this -

## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

# deb [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/) home


#AUTOMATIX REPOS START



#AUTOMATIX REPOS END
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) edgy 3v1n0


## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


## MAJOR BUG FIX UPDATES produced after the final release


## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)

---

### Post by lucky_chouhan on 2006-12-09
after i get this -

lakhan@root-desktop:~$ sudo apt-get install swf-player
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-1plf4) but 1.2.9-0.0 is to be installed
  swf-player: Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
              Depends: libcairo2 (>= 1.2.0) but 1.0.4-0ubuntu1 is to be installed
              Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.9) but 0.10.7-0ubuntu5 is to be installed
              Depends: libgstreamer0.10-0 (>= 0.10.9) but 0.10.6-0ubuntu2 is to be installed
              Depends: libgtk2.0-0 (>= 2.10.0) but 2.8.20-0ubuntu1 is to be installed
              Depends: libmad0 (>= 0.15.1b) but it is not going to be installed
              Depends: libpango1.0-0 (>= 1.13.5) but 1.12.3-0ubuntu3 is to be installed
              Depends: libswfdec0.3 (>= 0.3.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by lucky_chouhan on 2006-12-09
he thanks after i replace my sources.list finally synaptic manager is run.

thank you very much.

:) :) :) :)

---

### Post by lucky_chouhan on 2006-12-09
final i am play mp3 songs

:p :p :p :p

---

