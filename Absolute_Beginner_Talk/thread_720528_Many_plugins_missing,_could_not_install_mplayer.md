---
title: "Many plugins missing, could not install mplayer"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jis on 2008-03-10
I can't find xine-plugin, gxineplugin or moxilla-plugin-vlc Firefox suggests as video player plugins. I can't install mozilla-mplayer or mplayer. 

> $ sudo apt-get install mplayer
[sudo] password for jarnos:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages


---

### Post by jis on 2008-03-10
libggi2 1:2.2.1-5ubuntu1 is available.

> $ aptitude show mplayer-skins
No current or candidate version found for mplayer-skins
Package: mplayer-skins
State: not a real package


---

### Post by kwacka on 2008-03-10
1. what version are you using? (e.g. Gutsy?)

2. does 'sudo apt-get update' before trying to install mplayer help?

---

### Post by philinux on 2008-03-10
Use the terminal and post the output of

cat /etc/apt/sources.list

---

### Post by jis on 2008-03-10
kwacka, I am using Xubuntu 7.10 (aka Gutsy). 'sudo apt-get update' does not help, but gives this output:
> Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main Translation-en_US                                        
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/restricted Translation-en_US                        
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/web Translation-en_US                               
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/universe Translation-en_US                          
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/multiverse Translation-en_US                        
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/web Translation-en_US                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US                   
Get:4 [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release.gpg [189B]                                      
Ign [http://www.claws-mail.org](http://www.claws-mail.org) ./ Translation-en_US                                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:6 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/main Translation-en_US                                
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US                
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/web Translation-en_US                       
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/universe Translation-en_US                  
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US                
Get:7 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports Release.gpg [191B]                      
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/main Translation-en_US                              
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                                      
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                                
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/web Translation-en_US
Get:8 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Ign [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/web Translation-en_US
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy Release 
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates Release              
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports Release            
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://www.claws-mail.org](http://www.claws-mail.org) ./ Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                                          
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main Packages                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages                         
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/restricted Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources              
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-updates/restricted Packages          
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/main Packages              
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/restricted Packages        
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/universe Packages          
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-backports/multiverse Packages        
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/restricted Packages         
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy-proposed/universe Packages
Fetched 8B in 3s (2B/s)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release](http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by jis on 2008-03-10
philinux, there's the output of 'cat /etc/apt/sources.list':

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse web
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted web
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://www.claws-mail.org/ubuntu/gutsy/](http://www.claws-mail.org/ubuntu/gutsy/) ./
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe web


---

