---
title: "sudo apt-get update"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ryan73 on 2008-02-01
I enter 
sudo apt-get update
and receive 
ashley@ashley-desktop:~$ sudo apt-get update
[sudo] password for ashley:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done

I should say I am posting this on Ubuntu box so I have internet.
What start this was I can not download new applications
it says I need a internet connection...
I'm new to linux and I entered the cmd as advise from someone,

Any Thoughts or Ideas would be helpful
thank you

---

### Post by overdrank on 2008-02-01
> **ryan73 said:**
> I enter 
sudo apt-get update
and receive 
ashley@ashley-desktop:~$ sudo apt-get update
[sudo] password for ashley:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done

I should say I am posting this on Ubuntu box so I have internet.
What start this was I can not download new applications
it says I need a internet connection...
I'm new to linux and I entered the cmd as advise from someone,

Any Thoughts or Ideas would be helpful
thank you

Hi and welcome, could you post the out put of this command in the terminal ```
cat /etc/apt/sources.list
```

---

### Post by (((X))) on 2008-02-01
Enable all sources, except cd and sourcecode.
system->administration->sources

---

### Post by taurus on 2008-02-01
Just go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code, and the Cdrom in the bottom window.  Close it and press Refresh.  You should now be all set to install whatever else you want with synaptic, Add/Remove, or apt-get/aptitude.

---

### Post by ryan73 on 2008-02-01
man you guys are fast
ashley@ashley-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by ryan73 on 2008-02-01
now I got the following for cmd sudo apt-get update but am not able to download apps that is from changing Repositories
ashley@ashley-desktop:~$ sudo apt-get update
[sudo] password for ashley:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA       
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Fetched 5B in 1s (3B/s)  
Reading package lists... Done

---

### Post by Bluestick on 2008-02-01
Can some one help me out!!! 
read and see what it says at the end is this ok?


tom@tom-desktop:~$ sudo apt-get update
[sudo] password for tom:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/screenlets Translation-en_US           
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]        
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release [3686B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2718B]                      
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [26.9kB]                   
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources      
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/screenlets Packages [729B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources      
Get:12 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages [1488B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Get:13 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources [879B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Fetched 37.0kB in 2s (16.9kB/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
tom@tom-desktop:~$

---

### Post by ryan73 on 2008-02-02
you guys rock, fast reply, and helped me fix my issue fast.

thanks alot:guitar:

---

### Post by PmDematagoda on 2008-02-02
@Bluestick:- Open Software Sources in System>Administration>Software Sources, then go to the Third Party Software tab and disable all the entries. After that is done, close the window, you will be asked to reload the sources list, do that, your problem should then be solved.

---

