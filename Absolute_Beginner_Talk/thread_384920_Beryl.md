---
title: "Beryl"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-15
not sure if I am posting this correctly, but please understand my frustration.  I am trying to install Bery, and after a couple of hours of trying to find out how, using the terminal, and copy and pasting commands, this is what I got, and in the end, no Beryl !!!!! :( 

gettinoriginal@gettins-desktop:~$ sudo gedit /etc/apt.sources.list
sudo apt-get update && sudo apt-get install beryl
gettinoriginal@gettins-desktop:~$ sudo apt-get update && sudo apt-get install beryl
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:5 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Get:7 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg                           
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 9B in 6m0s (0B/s)                                 
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
gettinoriginal@gettins-desktop:~$ 

How does a newbie get Beryl :confused:

Sorry, I just read the warning by the moderator, disregard this post please, I do not want to install it.

---

### Post by adamchri on 2007-03-15
Sounds resonable, but when you change your mind start here:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

;-)

---

