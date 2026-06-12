---
title: "Problems with synaptic, update manager etc."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Pedal_Pusher on 2007-02-28
Hi,

I installed ubuntu (Edgy) for the first time last week.

I can't get any update method to work - they all timeout.  An example is :-

tom@Albany-amd:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB                          
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_GB                                    
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB                    
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB                              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done                  
tom@Albany-amd:~$ 

I have tried aptitude, apt-get, update manager and synaptic without success although I noticed one difference.  When I used synaptic first it said :-
1015 packages listed, 1015 installed, 0 broken. 0 to install/upgrade, 0 to remove.
It now says :-
4746 packages listed, 1015 installed, 0 broken. 0 to install/upgrade, 0 to remove.

When I first installed ubuntu my Firefox did not work.  I had to disable IPv6 within Firefox to get that going. Do I need to do something similar for software updates too ?

Any help will be much appreciated.

EDIT
I now think that the change in packages listed (1015 to 4746) happened when I changed the Settings / Repositories from UK to Main server - when i changed it back the number reverted to 1015.

All attempted updates still fail however.

End EDIT

---

### Post by STREETURCHINE on 2007-02-28
it looks like they may just be busy wait for a while and try again.

---

### Post by Pedal_Pusher on 2007-02-28
I have tried lots of times over the last few days with no joy at all.

I think it is a real problem with my configuration not just a transient workload peak.

---

### Post by Pedal_Pusher on 2007-02-28
Following advice in other threads I have now modified :-
/etc/hosts
/etc/modprobe.d/blacklist
/etc/modprobe.d/aliases
to comment out, blacklist and turn off references to ipv6

Firefox still works OK but synaptic, aptitude etc fail by timeout.

Help please .......

---

### Post by Repent on 2007-02-28
Wow thats really strange it worked OK for me.

joe203@joe203-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Fetched 7B in 7s (1B/s)                                                         
Reading package lists... Done
joe203@joe203-desktop:~$

---

### Post by Pedal_Pusher on 2007-02-28
Hi Repent,

I'm sure that it must work for a lot of people.  Otherwise a system which did not allow any updates or software upgrades or fixes would soon grind to a halt.

There do seem to be a number of us for whom it does not work however.  The recent threads / posts  from jjman, icyblue,  sandldan, ubunutgoz and hatien all seem to be related to this problem.

---

