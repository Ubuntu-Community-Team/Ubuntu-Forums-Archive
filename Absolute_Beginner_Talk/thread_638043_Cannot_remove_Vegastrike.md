---
title: "Cannot remove Vegastrike"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by montydonsheaddoctor on 2007-12-11
Hi guys I am having a problem with a game called Vegastike. It was installed using the  add/remove programs application. When it installed it reported some errors, so I decided to uninstall it and try again at some later date but it wont go, since then my update manager wont work , it says it is broken!
I have tried removing the offending packages in synaptic and have used the command Sudo apt-get install -f but to no avail.

---

### Post by taurus on 2007-12-11
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```
You probably have to run

```
sudo dpkg --configure -a
```

---

### Post by montydonsheaddoctor on 2007-12-12
running sudo apt-get  install -f gives the following


(update-desktop-database:6277): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing vegastrike (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 vegastrike
E: Sub-process /usr/bin/dpkg returned an error code (1)

Sudo apt-get update gives the following

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release.gpg                             
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Translation-en_GB                  
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB  
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B] 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB
Ign [http://download.videolan.org](http://download.videolan.org) sarge Release                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Ign [http://download.videolan.org](http://download.videolan.org) sarge/main Sources                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://download.videolan.org](http://download.videolan.org) sarge/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 4B in 0s (4B/s)  
Reading package lists... Done

---

