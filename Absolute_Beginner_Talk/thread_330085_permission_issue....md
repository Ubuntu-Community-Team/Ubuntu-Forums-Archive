---
title: "permission issue..."
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by theadventuresofanidealist on 2007-01-02
something happened after my last reboot, i everytime i try to open something from the menu system i get this error message: ' the configuration could not be loaded
                                                  you are not allowed to acess the system configuration. '
all this happened as i was trying to figure out an error in the samba winxp connection.
now i can't even see ther shared computer through xubuntu.

PLS HELP!

---

### Post by taurus on 2007-01-02
What's the output of this command from a terminal?

```
groups
```

---

### Post by theadventuresofanidealist on 2007-01-02
miguel adm dialout fax cdrom floppy audio dip video plugdev lpadmin scanner admin fuse samba

---

### Post by taurus on 2007-01-02
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by theadventuresofanidealist on 2007-01-02
miguel@ubuntu:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                 
Get:1 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy Release.gpg [191B]                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US        
Get:5 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy/universe Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US           
Get:7 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release.gpg [191B]                     
Ign [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Translation-en_US             
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release                                  
Get:10 [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports Release.gpg [191B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                           
Hit [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages             
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [191B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US                    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Hit 
[http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit 
[http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release                        
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                 
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                 
Hit 
[http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages                         
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources                              
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources                          
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US    
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy Release                                   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports Release                         
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/main Packages                   
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/restricted Packages             
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/universe Packages               
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/multiverse Packages             
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/main Sources		    
Hit 
[http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/restricted Sources              
Hit [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/universe Sources		    
Hit 
[http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 12B in 45s (0B/s)      Reading package lists... Done

miguel@ubuntu:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by taurus on 2007-01-02
Well, looks like sudo is working just fine for you!  Which GUI apps that you are having problems with?

---

### Post by theadventuresofanidealist on 2007-01-02
system menu:
services
shared folders
networking
sysinfo doesn't even start(prob different prob)
users and groups
time and date

these so far..

---

### Post by taurus on 2007-01-02
How about 

```
gksudo synaptic
```

---

### Post by theadventuresofanidealist on 2007-01-02
no problems there.

---

### Post by theadventuresofanidealist on 2007-01-02
HELP anybody?

---

