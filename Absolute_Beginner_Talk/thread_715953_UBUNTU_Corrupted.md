---
title: "UBUNTU: Corrupted?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-05
Upon discovering that I think, Adobe Flash Plugin in every browser has memory leaks, I decided to install a version of it from the Ubuntu Hardy Packages.

Unfortunately, I have to remove some libraries, I think many, because apt-get suggested me to do it.

Here's the log:

```
karlo@karlo-laptop:~$ sudo apt-get install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflashsupport
karlo@karlo-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-regex1.34.1 libgnutlsxx13 libtasn1-3-dev libgpg-error-dev
  libmagick++9c2a refblas3 libsuperlu3 gpp libxml1 libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  g++ g++-4.1 g++-4.2 k3d libc6-dev libc6-i686 libcairo2-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgnutls-dev
  libgtk2.0-dev libgts-0.7-5 liblzo2-dev libopencdk8-dev libpango1.0-dev
  libpng12-dev libpopt-dev libstdc++6-4.1-dev libstdc++6-4.2-dev libxft-dev
  libxml-dev libxml2-dev ubuntu-minimal zlib1g-dev
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 117MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
karlo@karlo-laptop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
karlo@karlo-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-regex1.34.1 libgnutlsxx13 libtasn1-3-dev libgpg-error-dev
  libmagick++9c2a refblas3 libsuperlu3 gpp libxml1 libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  g++ g++-4.1 g++-4.2 k3d libc6-dev libc6-i686 libcairo2-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgnutls-dev
  libgtk2.0-dev libgts-0.7-5 liblzo2-dev libopencdk8-dev libpango1.0-dev
  libpng12-dev libpopt-dev libstdc++6-4.1-dev libstdc++6-4.2-dev libxft-dev
  libxml-dev libxml2-dev ubuntu-minimal zlib1g-dev
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 117MB disk space will be freed.
Do you want to continue [Y/n]? n 
Abort.
karlo@karlo-laptop:~$ sudo synaptic
karlo@karlo-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-regex1.34.1 libgnutlsxx13 libtasn1-3-dev libgpg-error-dev
  libmagick++9c2a refblas3 libsuperlu3 gpp libxml1 libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  g++ g++-4.1 g++-4.2 k3d libc6-dev libc6-i686 libcairo2-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgnutls-dev
  libgtk2.0-dev libgts-0.7-5 liblzo2-dev libopencdk8-dev libpango1.0-dev
  libpng12-dev libpopt-dev libstdc++6-4.1-dev libstdc++6-4.2-dev libxft-dev
  libxml-dev libxml2-dev ubuntu-minimal zlib1g-dev
0 upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 117MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135447 files and directories currently installed.)
Removing g++ ...
Removing k3d ...
Removing libgts-0.7-5 ...
Removing libxml2-dev ...
Removing libgtk2.0-dev ...
Removing libpango1.0-dev ...
Removing libcairo2-dev ...
Removing libpng12-dev ...
Removing libxml-dev ...
Removing libxft-dev ...
Removing libgnutls-dev ...
Removing libfontconfig1-dev ...
Removing libfreetype6-dev ...
Removing zlib1g-dev ...
Removing libopencdk8-dev ...
Removing libpopt-dev ...
Removing liblzo2-dev ...
Removing libgcrypt11-dev ...
Removing libexpat1-dev ...
Removing ubuntu-minimal ...
Removing libc6-i686 ...
Removing g++-4.1 ...
Removing libstdc++6-4.1-dev ...
Removing g++-4.2 ...
Removing libstdc++6-4.2-dev ...
Removing libc6-dev ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
karlo@karlo-laptop:~$ sudo apt-get autoremove; sudo apt-get update; sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libboost-regex1.34.1 libice-dev libgnutlsxx13 x11proto-xext-dev
  libtasn1-3-dev libatk1.0-dev x11proto-kb-dev libgpg-error-dev
  x11proto-xinerama-dev libmagick++9c2a x11proto-render-dev refblas3 libxi-dev
  libxrender-dev libsuperlu3 libxdmcp-dev linux-libc-dev
  x11proto-composite-dev xtrans-dev x11proto-core-dev libxcursor-dev
  x11proto-randr-dev x11proto-damage-dev gpp libxext-dev libxdamage-dev
  libxml1 x11proto-input-dev x11proto-fixes-dev libxau-dev libxcomposite-dev
  libxrandr-dev libx11-dev libxfixes-dev libxinerama-dev libgtkglext1
The following packages will be REMOVED:
  gpp libatk1.0-dev libboost-regex1.34.1 libgnutlsxx13 libgpg-error-dev
  libgtkglext1 libice-dev libmagick++9c2a libsm-dev libsuperlu3 libtasn1-3-dev
  libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxi-dev libxinerama-dev libxml1
  libxrandr-dev libxrender-dev linux-libc-dev refblas3 x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev
0 upgraded, 0 newly installed, 37 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 34.5MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_PH
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_PH
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                     
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                    
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Get:4 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Ign http://www.getautomatix.com gutsy/main Translation-en_PH                   
Get:5 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                 
Get:6 http://www.virtualbox.org gutsy Release.gpg [189B]                       
Get:7 http://ph.archive.ubuntu.com gutsy Release.gpg [191B]                    
Get:8 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Get:9 http://repository.akirad.net akirad-gutsy Release.gpg [189B]             
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Get:10 http://www.getautomatix.com gutsy Release [6738B]                       
Ign http://security.ubuntu.com gutsy-security/main Translation-en_PH           
Ign http://archive.canonical.com gutsy/partner Translation-en_PH               
Ign http://download.tuxfamily.org gutsy/exaile Translation-en_PH               
Ign http://www.virtualbox.org gutsy/non-free Translation-en_PH                 
Ign http://ph.archive.ubuntu.com gutsy/main Translation-en_PH                  
Hit http://archive.ubuntu.com gutsy Release                                    
Ign http://repository.akirad.net akirad-gutsy/main Translation-en_PH           
Hit http://www.getautomatix.com gutsy/main Packages                            
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                      
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_PH     
Hit http://archive.canonical.com gutsy Release                                 
Ign http://javadesktop.org stable Release.gpg                                  
Get:11 http://download.tuxfamily.org gutsy Release [10.9kB]                    
Hit http://www.virtualbox.org gutsy Release                                    
Ign http://ph.archive.ubuntu.com gutsy/universe Translation-en_PH              
Hit http://archive.ubuntu.com gutsy/main Sources                               
Ign http://javadesktop.org stable/contrib Translation-en_PH                    
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_PH       
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://javadesktop.org stable Release                                      
Hit http://repository.akirad.net akirad-gutsy Release                          
Hit http://www.virtualbox.org gutsy/non-free Packages                          
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                      
Get:12 http://download.tuxfamily.org gutsy/exaile Packages [1227B]             
Hit http://archive.canonical.com gutsy/partner Sources                         
Ign http://javadesktop.org stable/contrib Packages                             
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_PH     
Hit http://repository.akirad.net akirad-gutsy/main Packages                    
Hit http://ppa.launchpad.net gutsy Release                                     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_PH               
Hit http://ppa.launchpad.net gutsy Release                                     
Ign http://ph.archive.ubuntu.com gutsy/restricted Translation-en_PH            
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://wine.budgetdedicated.com gutsy Release                              
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ph.archive.ubuntu.com gutsy/multiverse Translation-en_PH            
Hit http://repository.akirad.net akirad-gutsy/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Ign http://wine.budgetdedicated.com gutsy/main Packages                        
Ign http://ppa.launchpad.net gutsy/main Sources                                
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://javadesktop.org stable/contrib Packages                             
Ign http://ppa.launchpad.net gutsy/main Packages                               
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Ign http://ppa.launchpad.net gutsy/main Sources                                
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://ppa.launchpad.net gutsy/main Sources                                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://ppa.launchpad.net gutsy/main Packages                               
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Get:13 http://ph.archive.ubuntu.com gutsy-updates Release.gpg [191B]           
Hit http://ppa.launchpad.net gutsy/main Sources                                
Ign http://ph.archive.ubuntu.com gutsy-updates/main Translation-en_PH          
Ign http://ph.archive.ubuntu.com gutsy-updates/restricted Translation-en_PH    
Ign http://ph.archive.ubuntu.com gutsy-updates/universe Translation-en_PH      
Hit http://wine.budgetdedicated.com gutsy/main Sources                         
Ign http://ph.archive.ubuntu.com gutsy-updates/multiverse Translation-en_PH    
Hit http://wine.budgetdedicated.com gutsy/main Packages                        
Get:14 http://ph.archive.ubuntu.com gutsy-proposed Release.gpg [191B]          
Ign http://ph.archive.ubuntu.com gutsy-proposed/main Translation-en_PH         
Ign http://ph.archive.ubuntu.com gutsy-proposed/restricted Translation-en_PH   
Ign http://ph.archive.ubuntu.com gutsy-proposed/universe Translation-en_PH     
Ign http://ph.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_PH   
Get:15 http://ph.archive.ubuntu.com gutsy-backports Release.gpg [191B]         
Ign http://ph.archive.ubuntu.com gutsy-backports/main Translation-en_PH        
Ign http://ph.archive.ubuntu.com gutsy-backports/restricted Translation-en_PH  
Ign http://ph.archive.ubuntu.com gutsy-backports/universe Translation-en_PH    
Ign http://ph.archive.ubuntu.com gutsy-backports/multiverse Translation-en_PH  
Hit http://ph.archive.ubuntu.com gutsy Release                                 
Hit http://ph.archive.ubuntu.com gutsy-updates Release                         
Hit http://ph.archive.ubuntu.com gutsy-proposed Release                        
Hit http://ph.archive.ubuntu.com gutsy-backports Release                       
Hit http://ph.archive.ubuntu.com gutsy/main Packages                           
Hit http://ph.archive.ubuntu.com gutsy/universe Packages                       
Hit http://ph.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://ph.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://ph.archive.ubuntu.com gutsy/main Sources                            
Hit http://ph.archive.ubuntu.com gutsy/universe Sources                        
Hit http://ph.archive.ubuntu.com gutsy/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/main Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/main Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/main Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/multiverse Sources
Fetched 19.1kB in 1m10s (271B/s)
Reading package lists... Done
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_PH
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_PH
Ign http://javadesktop.org stable Release.gpg                                   
Ign http://ppa.launchpad.net gutsy Release.gpg                                  
Ign http://javadesktop.org stable/contrib Translation-en_PH                     
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                       
Ign http://javadesktop.org stable Release                                       
Ign http://javadesktop.org stable/contrib Packages                              
Ign http://ppa.launchpad.net gutsy Release.gpg                                  
Get:1 http://repository.akirad.net akirad-gutsy Release.gpg [189B]              
Ign http://ppa.launchpad.net gutsy/main Translation-en_PH                       
Hit http://ppa.launchpad.net gutsy Release                                      
Hit http://javadesktop.org stable/contrib Packages                              
Ign http://repository.akirad.net akirad-gutsy/main Translation-en_PH            
Get:2 http://www.getautomatix.com gutsy Release.gpg [189B]                      
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Get:4 http://archive.ubuntu.com gutsy Release.gpg [191B]                        
Get:5 http://www.virtualbox.org gutsy Release.gpg [189B]                        
Get:6 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                  
Get:7 http://archive.canonical.com gutsy Release.gpg [191B]                     
Get:8 http://ph.archive.ubuntu.com gutsy Release.gpg [191B]                     
Get:9 http://download.tuxfamily.org gutsy Release.gpg [189B]                    
Ign http://www.virtualbox.org gutsy/non-free Translation-en_PH                  
Hit http://ppa.launchpad.net gutsy Release                                      
Ign http://www.getautomatix.com gutsy/main Translation-en_PH                    
Ign http://ppa.launchpad.net gutsy/main Packages                                
Hit http://repository.akirad.net akirad-gutsy Release                           
Ign http://ppa.launchpad.net gutsy/main Sources                                 
Ign http://security.ubuntu.com gutsy-security/main Translation-en_PH            
Hit http://archive.ubuntu.com gutsy Release                                     
Ign http://ppa.launchpad.net gutsy/main Packages                                
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_PH                
Ign http://ppa.launchpad.net gutsy/main Sources                                 
Ign http://ph.archive.ubuntu.com gutsy/main Translation-en_PH                   
Ign http://download.tuxfamily.org gutsy/exaile Translation-en_PH                
Get:10 http://www.getautomatix.com gutsy Release [6738B]                        
Hit http://www.virtualbox.org gutsy Release                                     
Hit http://repository.akirad.net akirad-gutsy/main Packages                     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_PH      
Hit http://archive.ubuntu.com gutsy/main Sources                                
Ign http://archive.canonical.com gutsy/partner Translation-en_PH                
Hit http://www.getautomatix.com gutsy/main Packages                             
Hit http://repository.akirad.net akirad-gutsy/main Sources                      
Ign http://ph.archive.ubuntu.com gutsy/universe Translation-en_PH               
Hit http://ppa.launchpad.net gutsy/main Packages                                
Hit http://wine.budgetdedicated.com gutsy Release                               
Get:11 http://download.tuxfamily.org gutsy Release [10.9kB]                     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_PH        
Hit http://archive.ubuntu.com gutsy/restricted Sources                          
Hit http://www.virtualbox.org gutsy/non-free Packages                           
Hit http://archive.canonical.com gutsy Release                                  
Ign http://ph.archive.ubuntu.com gutsy/restricted Translation-en_PH             
Hit http://ppa.launchpad.net gutsy/main Sources                                 
Ign http://wine.budgetdedicated.com gutsy/main Packages                         
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_PH      
Hit http://archive.canonical.com gutsy/partner Packages                         
Get:12 http://download.tuxfamily.org gutsy/exaile Packages [1227B]              
Ign http://ph.archive.ubuntu.com gutsy/multiverse Translation-en_PH             
Hit http://ppa.launchpad.net gutsy/main Packages                                
Hit http://security.ubuntu.com gutsy-security Release                           
Hit http://wine.budgetdedicated.com gutsy/main Sources                          
Get:13 http://ph.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Hit http://ppa.launchpad.net gutsy/main Sources                                 
Hit http://security.ubuntu.com gutsy-security/main Packages                     
Hit http://wine.budgetdedicated.com gutsy/main Packages                         
Ign http://ph.archive.ubuntu.com gutsy-updates/main Translation-en_PH
Hit http://security.ubuntu.com gutsy-security/restricted Packages               
Ign http://ph.archive.ubuntu.com gutsy-updates/restricted Translation-en_PH     
Hit http://security.ubuntu.com gutsy-security/universe Packages                 
Ign http://ph.archive.ubuntu.com gutsy-updates/universe Translation-en_PH       
Hit http://archive.canonical.com gutsy/partner Sources                          
Hit http://security.ubuntu.com gutsy-security/multiverse Packages               
Ign http://ph.archive.ubuntu.com gutsy-updates/multiverse Translation-en_PH     
Hit http://security.ubuntu.com gutsy-security/main Sources                      
Get:14 http://ph.archive.ubuntu.com gutsy-proposed Release.gpg [191B]           
Hit http://security.ubuntu.com gutsy-security/restricted Sources                
Ign http://ph.archive.ubuntu.com gutsy-proposed/main Translation-en_PH          
Hit http://security.ubuntu.com gutsy-security/universe Sources                  
Ign http://ph.archive.ubuntu.com gutsy-proposed/restricted Translation-en_PH    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources                
Ign http://ph.archive.ubuntu.com gutsy-proposed/universe Translation-en_PH      
Ign http://ph.archive.ubuntu.com gutsy-proposed/multiverse Translation-en_PH    
Get:15 http://ph.archive.ubuntu.com gutsy-backports Release.gpg [191B]          
Ign http://ph.archive.ubuntu.com gutsy-backports/main Translation-en_PH         
Ign http://ph.archive.ubuntu.com gutsy-backports/restricted Translation-en_PH   
Ign http://ph.archive.ubuntu.com gutsy-backports/universe Translation-en_PH     
Ign http://ph.archive.ubuntu.com gutsy-backports/multiverse Translation-en_PH   
Hit http://ph.archive.ubuntu.com gutsy Release                                  
Hit http://ph.archive.ubuntu.com gutsy-updates Release                          
Hit http://ph.archive.ubuntu.com gutsy-proposed Release                         
Hit http://ph.archive.ubuntu.com gutsy-backports Release                        
Hit http://ph.archive.ubuntu.com gutsy/main Packages                            
Hit http://ph.archive.ubuntu.com gutsy/universe Packages                        
Hit http://ph.archive.ubuntu.com gutsy/restricted Packages                      
Hit http://ph.archive.ubuntu.com gutsy/multiverse Packages                      
Hit http://ph.archive.ubuntu.com gutsy/main Sources                             
Hit http://ph.archive.ubuntu.com gutsy/universe Sources                         
Hit http://ph.archive.ubuntu.com gutsy/restricted Sources                       
Hit http://ph.archive.ubuntu.com gutsy/multiverse Sources                       
Hit http://ph.archive.ubuntu.com gutsy-updates/main Packages                    
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Packages              
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-updates/main Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-proposed/main Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-proposed/multiverse Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/main Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://ph.archive.ubuntu.com gutsy-backports/main Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://ph.archive.ubuntu.com gutsy-backports/multiverse Sources
Fetched 19.1kB in 50s (376B/s)
Reading package lists... Done
karlo@karlo-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libboost-regex1.34.1 libice-dev libgnutlsxx13 x11proto-xext-dev
  libtasn1-3-dev libatk1.0-dev x11proto-kb-dev libgpg-error-dev
  x11proto-xinerama-dev libmagick++9c2a x11proto-render-dev refblas3 libxi-dev
  libxrender-dev libsuperlu3 libxdmcp-dev linux-libc-dev
  x11proto-composite-dev xtrans-dev x11proto-core-dev libxcursor-dev
  x11proto-randr-dev x11proto-damage-dev gpp libxext-dev libxdamage-dev
  libxml1 x11proto-input-dev x11proto-fixes-dev libxau-dev libxcomposite-dev
  libxrandr-dev libx11-dev libxfixes-dev libxinerama-dev libgtkglext1
The following packages will be REMOVED:
  gpp libatk1.0-dev libboost-regex1.34.1 libgnutlsxx13 libgpg-error-dev
  libgtkglext1 libice-dev libmagick++9c2a libsm-dev libsuperlu3 libtasn1-3-dev
  libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxi-dev libxinerama-dev libxml1
  libxrandr-dev libxrender-dev linux-libc-dev refblas3 x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev
0 upgraded, 0 newly installed, 37 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 34.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131233 files and directories currently installed.)
Removing gpp ...
Removing libatk1.0-dev ...
Removing libboost-regex1.34.1 ...
Removing libgnutlsxx13 ...
Removing libgpg-error-dev ...
Removing libgtkglext1 ...
Removing libsm-dev ...
Removing libice-dev ...
Removing libmagick++9c2a ...
Removing libsuperlu3 ...
Removing libtasn1-3-dev ...
Removing libxrandr-dev ...
Removing libxcursor-dev ...
Removing libxrender-dev ...
Removing libxinerama-dev ...
Removing libxi-dev ...
Removing libxdamage-dev ...
Removing libxcomposite-dev ...
Removing libxfixes-dev ...
Removing libxext-dev ...
Removing libx11-dev ...
Removing x11proto-damage-dev ...
Removing x11proto-composite-dev ...
Removing x11proto-fixes-dev ...
Removing x11proto-xext-dev ...
Removing libxau-dev ...
Removing libxdmcp-dev ...
Removing libxml1 ...
Removing linux-libc-dev ...
Removing refblas3 ...
Removing x11proto-core-dev ...
Removing x11proto-input-dev ...
Removing x11proto-kb-dev ...
Removing x11proto-randr-dev ...
Removing x11proto-render-dev ...
Removing x11proto-xinerama-dev ...
Removing xtrans-dev ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
karlo@karlo-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
karlo@karlo-laptop:~$ 
```

Everytime I ran flashplugin-nonfree, apt-get install, well I always receive that it has no installation candidate, and when I downloaded a package from Adobe's website, I always receive dependencies are not available, but when I downloaded those files, I can't install it, there's this error message.

Now, I tried to ignore everything and been very curios with another Window Manager. Enlightment17.

I followed the instructions here [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746) ... but the installation was not a success.

Here's the message:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-cvs: Depends: build-essential but it is not going to be installed
           Depends: libtool but it is not going to be installed
           Depends: giblib-dev but it is not going to be installed
           Depends: libimlib2-dev but it is not going to be installed
           Depends: libpopt-dev but it is not going to be installed
           Depends: libcurl3-dev or
                    libcurl4-openssl-dev but it is not going to be installed
           Depends: libbz2-dev but it is not going to be installed
           Depends: libid3tag0-dev but it is not going to be installed
           Depends: libpng12-dev but it is not going to be installed
           Depends: libtiff4-dev but it is not going to be installed
           Depends: libungif4-dev but it is not going to be installed or
                    libgif-dev but it is not going to be installed
           Depends: libjpeg62-dev but it is not going to be installed
           Depends: libssl-dev but it is not going to be installed
           Depends: libfontconfig1-dev but it is not going to be installed
           Depends: libfreetype6-dev but it is not going to be installed
           Depends: libxml2-dev but it is not going to be installed
           Depends: libsqlite3-dev but it is not going to be installed
           Depends: libasound2-dev but it is not going to be installed
           Depends: libxslt1-dev but it is not going to be installed
           Depends: libpam0g-dev but it is not going to be installed
E: Broken packages
```

I don't know if I should panic or not. HELP!!!:(:(:(

---

### Post by mikewhatever on 2008-03-05
Did you mean AdobeFlash:corrupted?

---

### Post by Rui Pais on 2008-03-05
Hi karl, 
as i said on  e17 from cvs thread, you mixed Gutsy with alpha hardy and you end up with one of the worst things that can happen, incorrect/conflicting libc6 package.

The only thing i can suggest, again not related with e17-cvs topic, its do a:
```
sudo apt-get install -f
``` 
and/or
open synaptic and go:
Custom Filters (bottom left) > Broken (top left) and double click on any red package listed. 
Sometimes users can go back to a sane install...

Good luck

---

