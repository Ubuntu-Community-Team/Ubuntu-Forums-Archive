---
title: "Update Problems"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-08-22
It seems my graphical updater has quit functioning, originally it stated I had 5 updates,that wouldn't run, so I did update and upgrade through the terminal it did install 1 update,but I guess "kept back the others" ?
Terminal output:

drakkor@drakkor:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get:2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]                        
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release                                     
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release                                     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release                         
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                               
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages               
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]               
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]             
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                               
Get:10 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                    
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                            
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [46.4kB]        
99% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                    
  Sub-process bzip2 returned an error code (2)
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                     
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [46.4kB]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages              
99% [Waiting for headers] [Connecting to packages.freecontrib.org] [Waiting for bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                    
  Sub-process bzip2 returned an error code (2)
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources                  
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources         
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages        
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources         
99% [15 Packages bzip2 0] [Waiting for headers] [Connecting to packages.freecontbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages                
  Sub-process bzip2 returned an error code (2)
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources       
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
99% [16 Sources bzip2 0] [Waiting for headers] [Connecting to packages.freecontrbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                 
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
99% [Waiting for headers] [Connecting to packages.freecontrib.org]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg                          
  Temporary failure resolving 'packages.freecontrib.org'
Fetched 57B in 20s (3B/s)                   
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
drakkor@drakkor:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  compiz compiz-gnome 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
drakkor@drakkor:~$

---

### Post by Drakkor on 2006-08-22
*bump*  Anyone?

---

### Post by confused57 on 2006-08-22
You could try opening Synaptic Package Manager, click on "Reload"
then "Mark All Upgrades" & "Apply"...SPM may be able to resolve any dependencies needed to install the upgrade.  May work, if you haven't already tried it.

I see you're still using beerorkid.com repository for Automatix instead of  getautomatix.com.

---

### Post by Drakkor on 2006-08-22
Thanks for the reply, confused57 , that's another problem I just seemed to have encounterded, Synaptic wouldn't even open ! With all this,it seemed like the system was getting corrupt, so fortunately I had a backup image that was made about 10 days ago and just re-imaged my whole drive back like it was, then ran the updater which now seems to work,and says it's up-to-date,and luckily I only have two programs to reinstall !!  :biggrin:
Edit" I thought getautomatix was the old one and beerorkid the new ??

---

### Post by confused57 on 2006-08-22
> **Drakkor said:**
> Thanks for the reply, confused57 , that's another problem I just seemed to have encounterded, Synaptic wouldn't even open ! With all this,it seemed like the system was getting corrupt, so fortunately I had a backup image that was made about 10 days ago and just re-imaged my whole drive back like it was, then ran the updater which now seems to work,and says it's up-to-date,and luckily I only have two programs to reinstall !!  :biggrin:
Edit" I thought getautomatix was the old one and beerorkid the new ??
Yes, sounds like your system was corrupted...I'd used the method I described to install a package that kept being held back in Update Manager.
Getautomatix.com is the newer one, beerorkid still works though:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_Ubuntu_6.06_Dapper_Drake](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_Ubuntu_6.06_Dapper_Drake)

---

