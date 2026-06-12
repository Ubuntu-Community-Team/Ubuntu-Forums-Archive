---
title: "My software soruces are not authenticated"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-06-23
Whenever I install software, the installer will always tell me that the software sources are not authenticated. That happens even when I install apps like "alien," "Epiphany Browser," and just about any application that I install (I guess all the applications that I install). 

How do I authenticate sofware sources?

---

### Post by Pragmatist on 2007-06-23
Please post your **/etc/apt/sources.list**

---

### Post by wersdaluv on 2007-06-23
Here  it is...

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse

deb http://jonnylamb.com debian/

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

deb http://archive.ubuntustudio.org/ubuntustudio feisty main

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

# LG3D repsoitories
deb http://javadesktop.org/lg3d/debian stable contrib

deb http://kubuntu.org/packages/kde-357 feisty main

## E17 repository “edevelop.org”

deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main 
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
```

:KS

---

### Post by taurus on 2007-06-23
What's the output message when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install alien
```

---

### Post by wersdaluv on 2007-06-23
```
sudo aptitude update
Get:1 http://archive.ubuntustudio.org feisty Release.gpg [189B]                 
Ign http://archive.ubuntustudio.org feisty/main Translation-en_PH               
Ign http://javadesktop.org stable Release.gpg                                   
Ign http://javadesktop.org stable/contrib Translation-en_PH                     
Get:2 http://jonnylamb.com debian/ Release.gpg [189B]                           
Get:3 http://edevelop.org edgy Release.gpg [189B]                               
Ign http://edevelop.org edgy/e17 Translation-en_PH                              
Hit http://archive.ubuntustudio.org feisty Release                              
Get:4 http://kubuntu.org feisty Release.gpg [189B]                              
Get:5 http://www.in.fh-merseburg.de feisty Release.gpg [189B]                   
Ign http://www.in.fh-merseburg.de feisty/main Translation-en_PH                 
Get:6 http://archive.ubuntu.com feisty Release.gpg [191B]                       
Ign http://archive.ubuntu.com feisty/main Translation-en_PH                     
Ign http://kubuntu.org feisty/main Translation-en_PH                            
Ign http://archive.ubuntu.com feisty/restricted Translation-en_PH               
Ign http://javadesktop.org stable Release                                       
Get:7 http://download.tuxfamily.org feisty Release.gpg [189B]                   
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_PH
Get:8 http://medibuntu.sos-sts.com feisty Release.gpg [189B]                    
Ign http://jonnylamb.com debian/ Translation-en_PH                              
Hit http://edevelop.org edgy Release                                            
Ign http://javadesktop.org stable/contrib Packages                              
Hit http://www.in.fh-merseburg.de feisty Release                                
Err http://www.in.fh-merseburg.de feisty Release                                
  
Ign http://archive.ubuntu.com feisty/universe Translation-en_PH                 
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_PH               
Get:9 http://archive.ubuntu.com feisty-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_PH             
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_PH       
Get:10 http://archive.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-security/main Translation-en_PH            
Hit http://archive.ubuntustudio.org feisty/main Packages                        
Hit http://kubuntu.org feisty Release                                           
Err http://kubuntu.org feisty Release                                           
  
Hit http://edevelop.org edgy/e17 Packages                                       
Hit http://jonnylamb.com debian/ Release                                        
Err http://jonnylamb.com debian/ Release                                        
  
Hit http://download.tuxfamily.org feisty Release                                
Hit http://javadesktop.org stable/contrib Packages                              
Hit http://edevelop.org edgy/e17 Sources                                        
Get:11 http://jonnylamb.com debian/ Release [1167B]                             
Ign http://jonnylamb.com debian/ Release                                        
Get:12 http://www.in.fh-merseburg.de feisty Release [1079B]                     
Ign http://www.in.fh-merseburg.de feisty Release                                
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_PH      
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_PH        
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_PH      
Get:13 http://kubuntu.org feisty Release [2887B]                                
Hit http://archive.ubuntu.com feisty Release                                    
Hit http://archive.ubuntu.com feisty-updates Release                            
Hit http://archive.ubuntu.com feisty-security Release                           
Ign http://kubuntu.org feisty Release                                           
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_PH                  
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages        
Ign http://jonnylamb.com debian/ Packages                                       
Ign http://www.in.fh-merseburg.de feisty/main Packages                          
Hit http://archive.ubuntu.com feisty/main Packages                              
Hit http://kubuntu.org feisty/main Packages                                     
Hit http://jonnylamb.com debian/ Packages                                       
Ign http://www.in.fh-merseburg.de feisty/main Sources                           
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_PH   
Hit http://archive.ubuntu.com feisty/restricted Packages             
Hit http://archive.ubuntu.com feisty/main Sources                    
Hit http://archive.ubuntu.com feisty/restricted Sources              
Hit http://www.in.fh-merseburg.de feisty/main Packages               
Hit http://archive.ubuntu.com feisty/universe Packages               
Hit http://archive.ubuntu.com feisty/universe Sources                
Hit http://archive.ubuntu.com feisty/multiverse Packages             
Hit http://archive.ubuntu.com feisty/multiverse Sources              
Hit http://archive.ubuntu.com feisty-updates/main Packages           
Hit http://archive.ubuntu.com feisty-updates/restricted Packages     
Hit http://archive.ubuntu.com feisty-updates/main Sources            
Hit http://medibuntu.sos-sts.com feisty Release                      
Hit http://www.in.fh-merseburg.de feisty/main Sources                
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/main Sources
Hit http://archive.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/universe Sources
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Sources
Ign http://medibuntu.sos-sts.com feisty/free Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages                       
Hit http://medibuntu.sos-sts.com feisty/free Sources                            
Hit http://medibuntu.sos-sts.com feisty/non-free Sources                        
Fetched 5707B in 7s (729B/s)                                                    
Reading package lists... Done
W: GPG error: http://jonnylamb.com debian/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C18AFB9F2E039402
W: GPG error: http://www.in.fh-merseburg.de feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB210090B029CB84
W: GPG error: http://kubuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems

```

```
sudo aptitude install alien
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```
*I already have alien installed

---

