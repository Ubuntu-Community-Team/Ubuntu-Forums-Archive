---
title: "error in updating repositories..."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by jatiesch on 2008-02-02
hi i have a problem in using update manager and add/remove...
i have added a snapshot...
plz help...

---

### Post by Shiva-Shinken on 2008-02-02
I am a beginner Linux user also, so my advice may not be accurate.  Try launching the terminal and type ```
sudo apt-get update
```  Hope that works, plz let me know how it goes.

CC

---

### Post by Julita on 2008-02-02
Please, do the command that has been suggested by Shiva,
as well as the following:

sudo apt-get -f install
sudo apt-get upgrade
sudo apt-get dist-upgrade

also try
dpkg --configure

---

### Post by jan quark on 2008-02-02
go to system > administration > sources
you will find it :)

if they are unchecked

check all available sources except the last ones, cd and source code, 

run

sudo apt-get update 

and try to update again

---

### Post by Julita on 2008-02-02
If something wrong with the sources, than you can edit them by typing

gsudo gedit /etc/apt/sources.list

---

### Post by jan quark on 2008-02-02
```
gksudo gedit /etc/apt/sources.list
```
this is correct

---

### Post by jatiesch on 2008-02-02
thanks...but i have already checked all the repositories in source list...
so that is not a problem..

sudo apt-get update result:
[I]
jatiesch@jatiesch-desktop:~$ sudo apt-get update
[sudo] password for jatiesch:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN           
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN       
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IN     
  Could not resolve 'security.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_IN               
  Could not resolve 'archive.canonical.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Translation-en_IN            
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Translation-en_IN              
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Translation-en_IN            
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve 'in.archive.ubuntu.com'
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_IN
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Translation-en_IN       
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN 
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Translation-en_IN   
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN 
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release.gpg                
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Translation-en_IN     
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Translation-en_IN 
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IN                  
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN              
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IN            
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN            
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_IN      
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_IN          
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN    
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN    
  Could not resolve 'archive.ubuntu.com'
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Packages
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
  Could not resolve 'archive.canonical.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Sources
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
  Could not resolve 'archive.canonical.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages      
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Sources       
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Sources 
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Packages  
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Sources   
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Sources 
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages
  Could not resolve 'in.archive.ubuntu.com'
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages         
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages     
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages   
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages   
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages 
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Sources
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Sources
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-amd64/Packages.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-amd64/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  Could not resolve 'archive.canonical.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-amd64/Packages.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-amd64/Packages.gz)  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]

---

### Post by jatiesch on 2008-02-02
also i ran commands as mentioned in the earlier posts...
these are the results:
[I]jatiesch@jatiesch-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jatiesch@jatiesch-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jatiesch@jatiesch-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I]

---

### Post by jatiesch on 2008-02-02
anybody??

---

### Post by Julita on 2008-02-03
It may be that the problem is in the server you have chosen to download from. In the Synaptic go to the "Repositories" and try to change the server.

---

### Post by dariusdwtt on 2008-04-04
I have the same problem  :confused:

If you find anything that helps please send me a message.

Darius

---

### Post by Oldsoldier2003 on 2008-04-04
> **dariusdwtt said:**
> I have the same problem  :confused:

If you find anything that helps please send me a message.

Darius

Make sure you are not behind a proxy server. then enable the repos again in software sources and try again.

---

### Post by dariusdwtt on 2008-04-04
No proxy. Gonna try DNS settings as seen in another thread... ?

---

### Post by Oldsoldier2003 on 2008-04-04
> **dariusdwtt said:**
> No proxy. Gonna try DNS settings as seen in another thread... ?

yes if you dont have a proxy check your dns and make sure you aren't firewalled from http access. ( I won't make the assumption that you are posting from the same box)

---

### Post by dariusdwtt on 2008-04-04
yip same box. dualboot XP.
can only use command line need to install driver for chipset.
have no idea what to do next.......

any suggestions?

---

### Post by dariusdwtt on 2008-04-04
modem must b supported, said something during the install about modem seen and hooked up...(not sure about terminology :))

---

