---
title: "ubuntu repos down?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by penquin on 2007-12-13
are the ubuntu repos down?  I keep getting the message that"The repository might be no longer available"

---

### Post by dptxp on 2007-12-13
Which server are you trying ? Try another one.

---

### Post by subs on 2007-12-13
> **penquin said:**
> are the ubuntu repos down?  I keep getting the message that"The repository might be no longer available"



u must have made an entry to the repository list... and added some new source so that u could install some particular software..... perhaps thats what it causing the problem

---

### Post by ctyc on 2007-12-13
It seems this is the repos in question:


[http://packages.medibuntu.org/dists/gutsy/Release.gpg](http://packages.medibuntu.org/dists/gutsy/Release.gpg)
[http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_CA.bz2](http://packages.medibuntu.org/dists/gutsy/free/i18n/Translation-en_CA.bz2)
[http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_CA.bz2](http://packages.medibuntu.org/dists/gutsy/non-free/i18n/Translation-en_CA.bz2)

---

### Post by penquin on 2007-12-13
how can those be the culprit?

---

### Post by rsambuca on 2007-12-13
Post the output of 

```
sudo apt-get update
```

and 

```
cat /etc/apt/sources.list
```

---

### Post by penquin on 2007-12-14
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Get:3 [http://repository.debuntu.org](http://repository.debuntu.org) gutsy Release.gpg [189B]                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:6 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]                 
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:7 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas Release.gpg [307B]             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:9 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Ign [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Release.gpg                                       
Ign [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Translation-en_US                                 
Ign [http://repository.debuntu.org](http://repository.debuntu.org) gutsy/multiverse Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/web Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas/all Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Release                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/web Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]         
Get:12 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas Release [6736B]               
Hit [http://www.mpe.mpg.de](http://www.mpe.mpg.de) ./ Packages                                          
Hit [http://repository.debuntu.org](http://repository.debuntu.org) gutsy Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/web Translation-en_US         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/web Translation-en_US          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://ubuntu.org.ua](http://ubuntu.org.ua) getdeb/ Release.gpg                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://repository.debuntu.org](http://repository.debuntu.org) gutsy/multiverse Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Get:14 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) gutsy-seveas/all Packages [14B]            
Ign [http://ubuntu.org.ua](http://ubuntu.org.ua) getdeb/ Translation-en_US                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-security/restricted Packages            
Ign [http://ubuntu.org.ua](http://ubuntu.org.ua) getdeb/ Release                                       
Ign [http://ubuntu.org.ua](http://ubuntu.org.ua) getdeb/ Packages                                      
Hit [http://ubuntu.org.ua](http://ubuntu.org.ua) getdeb/ Packages                                      
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                          
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Fetched 7068B in 4m5s (29B/s)                                
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/gutsy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

# Repositorio del Emesene

# Repositorios de Linex para Gambas 2

# Repositorios comerciales de canonical
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

---

### Post by DeLaNooch on 2007-12-14
Obviously that Wine repo is down.  Don't know enough to know what's going on with that us.archive.ubuntu repo.  I am interested in seeing what the solution to this problem is...

---

### Post by OffAxis on 2007-12-14
ya, it's the 
**[http://wine.budgetdedicated.com](http://wine.budgetdedicated.com)**
line that's giving you issues (at least in part)
you can comment it out it in your
**/etc/apt/sources.lst**
and run
```
sudo apt-get update

```
or just wait for it to come back online.

I think your wine line is wrong, though.

would you please post your
**/etc/apt/sources.lst**

and any files in
**/etc/apt/sources.list.d/**

my wine sources in
**/etc/apt/sources.list/d/winehq.list**
read
```
deb http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
deb-src http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"

```

you could always just comment your winehq lines out and re-run the commands off their website.

---

### Post by penquin on 2007-12-15
it wasn't the wine repo.  I did solve it by deleteing the contents of sources.list and putting in a fresh sources.list contents.

---

