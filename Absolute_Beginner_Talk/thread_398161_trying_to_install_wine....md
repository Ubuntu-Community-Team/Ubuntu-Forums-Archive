---
title: "trying to install wine..."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-03-31
I ve tryin to install wine...
it seems everything to works just fine...but at the end i always get the same thing...have a look..and if anybody can tell me i would appreciate..

hvasss@hvasss-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:5788): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
hvasss@hvasss-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg: requesting key 387EE263 from hkp server subkeys.pgp.net
gpg: key 387EE263: public key "Scott Ritchie <scott@open-vote.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
hvasss@hvasss-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg: requesting key 387EE263 from hkp server subkeys.pgp.net
gpg: key 387EE263: "Scott Ritchie <scott@open-vote.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
hvasss@hvasss-desktop:~$ sudo apt-get update
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release [739B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Get:6 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:7 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy Release                                  
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US       
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates Release                          
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Get:13 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages [1317B]              
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Get:14 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources [639B]                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release.gpg                       
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf/free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
99% [Connecting to packages.freecontrib.org (88.191.33.6)]

---

### Post by Zuuswa on 2007-03-31
well it appears that you cannot reach the server for the package list . . . try a differant repository for wine, that is what I would do.

---

