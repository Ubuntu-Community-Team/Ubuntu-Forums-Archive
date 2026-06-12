---
title: "Automatic Update error"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by alans on 2007-07-06
I am a new user.  When new updates icon shows the installation is always followed by an error message as follows - "E: clamav-base: subprocess post-installation script returned error exit status 1"  There then follows a message indicating that not all changes or updates succeeded etc.

There appears to be no operating problem.

I would be grateful for advice.

alans

---

### Post by shrift on 2007-07-06
In a terminal copy and paste this command:
```
sudo aptitude upgrade
```

Please paste the output of that here.

---

### Post by alans on 2007-07-08
Password:

Terminal asks for a password, but will not accept my password when I type it in.

I am grateful for your further advice

Alans

---

### Post by taurus on 2007-07-08
You won't see any echo on the screen when you type in your password so just type it in and hit Return.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by shrift on 2007-07-09
> **alans said:**
> Password:

Terminal asks for a password, but will not accept my password when I type it in.

I am grateful for your further advice

Alans

I don't know if this is working for you now, I hope it is... You need to be the root user, or the primary user on the system to do this. Are you? That or you need to have the system admin give you permissions so that you can use aptitude. 

OR, you typed your password wrong. : )

---

### Post by alans on 2007-07-09
Many thanks.  Copied below is what Terminal produced:

Get:1 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release.gpg [191B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Translation-en_GB                       
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release                                      
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]                    
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB              
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]  
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB            
Get:9 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_GB      
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                         
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Get:11 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 6409B in 1s (4797B/s)
Reading package lists... Done
aes@aes-desktop:~$ 


I am grateful for your continued advice

Alans

---

### Post by shrift on 2007-07-09
That is looking good. Now try running "sudo aptitude upgrade". Then post the output of that if it doesn't work.

---

### Post by alans on 2007-07-09
Many thanks.  Done that - output below :-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
aes@aes-desktop:~$ 


Hope this makes sense.
I am grateful for your help
Alans

---

### Post by shrift on 2007-07-09
Try running ```
sudo aptitude purge clamav
``` If it seems like that works, then try installing it again. If not post the output of the terminal again.

It looks like this error is limited to clamav, so any other packages should install/upgrade just fine.

---

### Post by halesquad on 2007-07-09
stephen@stephen-desktop:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
stephen@stephen-desktop:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]                    
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB [4827B]        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB           
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB       
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                   
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_GB
Get:7 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                 
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                     
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_GB                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_GB            
Get:10 [http://debs.peadrop.com](http://debs.peadrop.com) edgy Release.gpg [189B]                          
Ign [http://debs.peadrop.com](http://debs.peadrop.com) edgy/backports Translation-en_GB                    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                      
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB              
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B] 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_GB               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_GB        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB    
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release.gpg [191B]         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB  
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                           
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                              
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages  
Hit [http://debs.peadrop.com](http://debs.peadrop.com) edgy Release                            
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                            
Hit [http://debs.peadrop.com](http://debs.peadrop.com) edgy/backports Packages                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages           
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages               
Fetched 6602B in 9s (731B/s)                                                    
Reading package lists... Done
stephen@stephen-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
stephen@stephen-desktop:~$ 



i get the above happen with that error message. Do you know any code that i could use to get rid of this?

Thanks 

Stephen

---

### Post by alans on 2007-07-09
output follows:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base


Unable to follow up tonight.  Will look again tomorrow.

Many thanks for your interest and help
Alans

---

### Post by shrift on 2007-07-09
> **alans said:**
> output follows:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base


Unable to follow up tonight.  Will look again tomorrow.

Many thanks for your interest and help
Alans

Alans, it doesn't look like you ran the command "sudo aptitude purge" because it says in the manager there that no programs will be removed... Are you sure you did that? Sorry to double check.

Alans and Halesquad try running this command: ```
sudo apt-get install -f
```

Also, if you can please include the command you entered and the output following it, if it doesn't seem to fix anything.

---

### Post by shrift on 2007-07-09
Halesquad, where did you get the package "oss-linux" ubuntu does not have such a package in any of it's main repositories. Also, what are you trying to get to work by installing it?

---

### Post by halesquad on 2007-07-09
i don't know where i got it from and i am unsure what it runs but i will gladly take your advise and remove it if you give me the right code. thanks

---

### Post by halesquad on 2007-07-09
stephen@stephen-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-console tetex-base libgtk1.2 libglib1.2 libsdl-gfx1.2-4 libflac++5c2
  libkdegames1 libsdl-net1.2 libtidy-0.99-0 libt1-5 libsdl-ttf2.0-0
  libsdl-pango1 frozen-bubble-data python-wxversion libgtk1.2-common
  libsdl-perl planetpenguin-racer-data libsdl-mixer1.2 fb-music-high
  python-wxgtk2.6 tex-common libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
stephen@stephen-desktop:~$

---

### Post by alans on 2007-07-10
Entered command and output follows:

aes@aes-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libofx3 libgtkhtml3.8-15 guile-1.6 libreadline5-dev libosp5
  libcrypt-ssleay-perl libncurses5-dev libdate-manip-perl slib libffi4
  libgwrap-runtime0-dev libgwrap-runtime0 libgsf-gnome-1-114 libffi4-dev
  libfinance-quote-perl g-wrap guile-1.6-slib guile-g-wrap guile-1.6-dev
  libhtml-tableextract-perl guile-library
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
aes@aes-desktop:~$ 

Hope this helps for further advice.
Many thanks
Alans

---

### Post by kitterma on 2007-07-12
The solution to the chown: cannot access `/var/run/clamav': No such file or directory problem is:

sudo mkdir /var/run/clamav

Then try to install again.

---

### Post by alans on 2007-07-12
Thank you for your advice.  Forgive me for being thick - do you mean re-install Ubuntu from disk?

alans

---

### Post by kitterma on 2007-07-12
No problem.  

No, I mean reinstall clamav.

The command line for it would be:

sudo apt-get install clamav

---

### Post by alans on 2007-07-13
Done those.  Now wait for next automatic update and see result.

I am grateful for your advice.

alans

---

### Post by alans on 2007-07-23
Automatic updates now being installed with no problem.  Thanks for the help and advice.
Alans

---

