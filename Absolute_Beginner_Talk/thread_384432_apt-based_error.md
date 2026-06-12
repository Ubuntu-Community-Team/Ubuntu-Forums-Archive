---
title: "apt-based error"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by chebert on 2007-03-14
Hello everyone,
I must say I had a lot of help with my last question I previously posted.  Now, my second question, this time in a new thread (I asked a new question in an ongoing thread last time)!
I am trying to load  Gdesklets from Automatix2.  I get a fatal error message saying an apt-based error occurred and instillation was unsuccessful.  
Now what do I do?
chebert

---

### Post by bapoumba on 2007-03-14
Please open a terminal (Accessories > Terminal) and run:
```
sudo aptitude update
cat /etc/apt/sources.list
```
and paste in here the complete output to these to commands.

---

### Post by chebert on 2007-03-14
Thanks, here it is...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Translation-en_US                                
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]                            
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages                                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources                                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages                                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources                                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                                 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                                            
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                                  
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                                   
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                                   
  403 Forbidden
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US                        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US                         
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                                           
Fetched 1908B in 17s (110B/s)                                                                    
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

---

### Post by bapoumba on 2007-03-14
Try:
```
sudo dpkg --configure -a
```
and paste the error, if any.

paste also the output to:
```
cat /etc/apt/sources.list
```

---

### Post by chebert on 2007-03-14
Sorry I'm slow to respond.  I'm at work.
chebert



chebert7@chebert7-desktop:~$ sudo dpkg --configure -a
chebert7@chebert7-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END

---

### Post by chebert on 2007-03-14
Thanks for your help.  I'll have to pick this up tomorrow.
chebert

---

### Post by bapoumba on 2007-03-14
Okay, there was another command:
```
sudo dpkg --configure -a
```
and also paste the error.

---

### Post by chebert on 2007-03-15
Nothing happens.  
I have an AMD 64 processor.  I received the current version of ubuntu from a friend, I downloaded from a live cd.  I noticed in my exploring that there is a version of ubuntu for amd processors.  How do I check if I have the correct version, processor specific, loaded?  Or does this even matter?
CH

---

### Post by bapoumba on 2007-03-15
you can check that with **uname -a**

---

### Post by Shampyon on 2007-03-16
I'm having a similar problem.

I tried to install Crossover Office and I think the install went wrong. Now when I try to access apt in any form I get that same error: 
*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. *

When I run the command (as root) I get this error:
*The Wine environment directory 'home/myusername/.cxoffice/win98' does not belong to you. Please check the value of $HOME and/or use 'su'*

What's the best solution here?
[I]
Edit:[/I] I can't believe this. Twenty seconds after I post, I figure it out. I installed it from a .deb, so I simply tried to install the .deb again, without removing the previous installation. It failed of course, but managed to put the package back into Synaptic, from where i was able to do a complete removal. No everything's hunky-dory again :)

---

