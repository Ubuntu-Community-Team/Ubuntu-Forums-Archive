---
title: "[SOLVED] Humongus screw-up"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-11-16
I have been using version 7.10 since the upgrade became available. Now I need to repair it and have no idea where to begin.

The problem started with a message from "Update manager" that there are 3 updates available, when I hit the "Install Updates" button I get the message that
> Not all updates can be installed and then--
> Run a partial upgrade, to install as many updates as possibleThen when I try to run the upgrade I get-- > Please insert 'Ubuntu 6.06_Dapper Drake_ -Release i386 (20060531.2)' into the drive ' /cdrom'Then the _upgrade_ aborts.

The last thing I did before this problem was mistakenly put a DVD  with the 6.06 install on it into the drive. I thought it was the "The official Ubunbtu Book" but it was an installation disk that came with the book. I did not actually get into the installation process but something obviously got messed up.

By the way, the 7.10 installation is still working as far as I can tell. Please help.

---

### Post by wolfen69 on 2007-11-16
try this in terminal:
```
dpkg --configure -a
```

---

### Post by Inxsible on 2007-11-16
> **wolfen69 said:**
> try this in terminal:
```
dpkg --configure -a
```you will have to add a sudo in front of that

---

### Post by kindafunnylookin on 2007-11-16
peter@Gutsy7_10:~$ sudo dpkg --configure -a
peter@Gutsy7_10:~$ 

 Still getting the same messages from Update Manager

---

### Post by kindafunnylookin on 2007-11-16
bump

---

### Post by Inxsible on 2007-11-16
try ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by kindafunnylookin on 2007-11-16
This is the output:

> peter@Gutsy7_10:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2) dapper/main Translation-en_US
Ign cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2) dapper/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Translation-en_US       
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial Release                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy Release.gpg                             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Packages                 
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy-commercial/main Packages      
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Packages             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Sources
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Packages
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/free Sources
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) gutsy/non-free Sources
  404 Not Found
Fetched 6B in 1s (3B/s)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
peter@Gutsy7_10:~$ 


---

### Post by maybeway36 on 2007-11-16
Go to System>Administration>Software Sources and uncheck any CD-ROM source on the "Third Party" tab. Then refresh the sources (sudo apt-get update) again.

---

### Post by Inxsible on 2007-11-16
> **maybeway36 said:**
> Go to System>Administration>Software Sources and uncheck any CD-ROM source on the "Third Party" tab. Then refresh the sources (sudo apt-get update) again.
yeah you need to remove you CD as the resource - especially since you have Dapper CD's enabled.

---

### Post by kindafunnylookin on 2007-11-16
OK I did  what you suggested after unchecking a Dapper CD source as advised and ended up with:```
peter@Gutsy7_10:~$ sudo apt-get update
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]
Ign http://www.getautomatix.com gutsy/main Translation-en_US                   
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://archive.canonical.com gutsy-commercial Release.gpg                  
Ign http://archive.canonical.com gutsy-commercial/main Translation-en_US       
Get:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Hit http://www.getautomatix.com gutsy Release                                  
Ign http://medibuntu.sos-sts.com gutsy Release.gpg                             
Ign http://medibuntu.sos-sts.com gutsy/free Translation-en_US                  
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://www.getautomatix.com gutsy/main Packages                            
Get:4 http://archive.canonical.com gutsy Release.gpg [191B]          
Ign http://archive.canonical.com gutsy/partner Translation-en_US     
Ign http://archive.canonical.com gutsy-commercial Release            
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US     
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US     
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]     
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US   
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://medibuntu.sos-sts.com gutsy/non-free Translation-en_US    
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://archive.canonical.com gutsy Release                       
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]             
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
Ign http://medibuntu.sos-sts.com gutsy Release                                 
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Ign http://archive.canonical.com gutsy-commercial/main Packages                
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                          
Hit http://archive.ubuntu.com gutsy-updates Release                  
Hit http://archive.ubuntu.com gutsy-backports Release                          
Ign http://medibuntu.sos-sts.com gutsy/free Packages                           
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Ign http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.ubuntu.com gutsy/main Packages                    
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Sources
Ign http://medibuntu.sos-sts.com gutsy/non-free Packages
Ign http://medibuntu.sos-sts.com gutsy/free Sources
Err http://archive.canonical.com gutsy-commercial/main Packages
  404 Not Found
Ign http://medibuntu.sos-sts.com gutsy/non-free Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/multiverse Sources               
Hit http://archive.ubuntu.com gutsy-updates/main Packages            
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages      
Hit http://archive.canonical.com gutsy/partner Packages
Err http://medibuntu.sos-sts.com gutsy/free Packages
  404 Not Found
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Err http://medibuntu.sos-sts.com gutsy/non-free Packages
  404 Not Found
Err http://medibuntu.sos-sts.com gutsy/free Sources
  404 Not Found
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-backports/main Packages
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Err http://medibuntu.sos-sts.com gutsy/non-free Sources
  404 Not Found
Fetched 6B in 1s (3B/s)  
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
peter@Gutsy7_10:~$ 
```

---

### Post by mips on 2007-11-18
Disable the medibuntu repositories and it should work fine. Might as well disable the automatix ones as well just in case.

---

