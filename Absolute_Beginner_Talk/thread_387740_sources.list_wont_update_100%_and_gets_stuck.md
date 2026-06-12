---
title: "sources.list wont update 100% and gets stuck"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-03-18
I keep having trouble updating my sources list and think I may have added some unnessary repositories, oops what a nOoB sorry.  I am trying to search for my probs but this is all completely new.   I wish Willy G had never came out with MSoft as this is alot like the old DOS system I used in teh 80's but still different, with msoft crap you dont code at all........anyway here is my current sources.list (I am running ubuntu 6.10  AMD 64 version )  Thank you for your patience!
I keep getting stuck at 99% at 
> 
99% [Connecting to packages.freecontrib.org (88.191.33.6)]  


> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse 

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse 

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse 

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main 
deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) dapper main 

# Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free 

# Repository for wine
deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) dapper main 
deb-src [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) dapper main 

#Compiz
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) edgy main-edgy 
deb-src [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) edgy main-edgy 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main 

#Emulators
deb [http://ma.ath.cx/debian-emu-rep](http://ma.ath.cx/debian-emu-rep) binary/ 
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main



---

### Post by DougieFresh4U on 2007-03-18
Let me ask, why do you have dapper AND edgy repo's? Which one are you running?

---

### Post by Kobalt on 2007-03-18
wow, that sources.list is a mess... you should clean that up a little bit I think, and it'll solve your problem.

---

### Post by DougieFresh4U on 2007-03-18
> **Kobalt said:**
> wow, that sources.list is a mess... you should clean that up a little bit I think, and it'll solve your problem.

Exactly, my point!! Decide which distro version you want and eliminate the other.

---

### Post by pebs on 2007-03-22
Hi,

I'm having a similar problem, although I think my sources.list are fine:
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

```
The problem is that the first time I do an update, it hangs-up here:
```

(...)
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
99% [10 Packages bzip2 0]

```
After Ctrl+c and update again, it updates correctly, but this appears:
```

(...)
Fetched 3739kB in 1m24s (44.3kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
Apart from the warnings, the repos. are updated ok, and from the third time onwards it updates without warnings. This happens every time I type the first "sudo apt-get update" after turning on my PC.

Anyone knows what the problem might be? Thanks!

---

### Post by john rose on 2007-03-26
I'm having similar problems re communicating with packages.freecontrib.org. It specied dapper on sources.list. This is weird considering I have installed edgy (i.e. not upgraded from dapper).

Sources.list is:



 I then changed the references in sources.list to edgy and tried again with the same result.
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Get:3 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Get:9 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Get:10 [http://debian.space-based.de](http://debian.space-based.de) experimental Release.gpg [189B]            
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Translation-en_US           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                          
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                            
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_US                 
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Err [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages              
Get:12 [http://debian.space-based.de](http://debian.space-based.de) experimental Release [718B]                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Packages                    
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Sources                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental/main Packages                    
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental/main Sources                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
99% [Connecting to packages.freecontrib.org (88.191.33.6)]                     
admin@john-laptop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Get:3 [http://debian.space-based.de](http://debian.space-based.de) experimental Release.gpg [189B]             
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
Get:10 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Err [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                          
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Get:12 [http://debian.space-based.de](http://debian.space-based.de) experimental Release [718B]                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources                       
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental Release                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources                     
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Packages                    
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages                
Ign [http://debian.space-based.de](http://debian.space-based.de) experimental/main Sources                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental/main Packages                    
Hit [http://debian.space-based.de](http://debian.space-based.de) experimental/main Sources                     
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg                           
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg      
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 917B in 12m0s (1B/s)                              
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/edgy/non-free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Reading package lists... Done
W: GPG error: [http://debian.space-based.de](http://debian.space-based.de) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EB020D4677AFC5B7
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

Obviously there is a problem with debian.space-based.de repositories. I'm now trying to remember why I put them there! However, I'm more interested in why the timeout to packages.freecontrib.org. Their lines in sources.list have been there for weeks but the problem has only arrived in the last few days. Any ideas?

---

### Post by zvacet on 2007-03-26
[B] gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -[/B]

In your case
gpg --keyserver hkp://subkeys.pgp.net --recv-keys **EB020D4677AFC5B7**
gpg --export --armor **EB020D4677AFC5B7** |  sudo apt-key add -

---

### Post by tatster on 2007-07-09
> **pebs said:**
> Hi,

I'm having a similar problem, although I think my sources.list are fine:
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

```
The problem is that the first time I do an update, it hangs-up here:
```

(...)
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
99% [10 Packages bzip2 0]

```
After Ctrl+c and update again, it updates correctly, but this appears:
```

(...)
Fetched 3739kB in 1m24s (44.3kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
Apart from the warnings, the repos. are updated ok, and from the third time onwards it updates without warnings. This happens every time I type the first "sudo apt-get update" after turning on my PC.

Anyone knows what the problem might be? Thanks!

I have exactly the same symptoms as Pebs.

Any ideas anyone???

Thanks,

Tatster.

---

