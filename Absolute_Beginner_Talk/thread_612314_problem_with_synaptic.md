---
title: "problem with synaptic"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-11-13
E: emifreq-applet: subprocess post-installation script returned error exit status 2

i got this after trying to install a few programs, what does it mean?

---

### Post by rudeboyskunk on 2007-11-13
Not too sure, but open up a terminal and fire away these two commands:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Let us know if either of those gives you an error.  Also, make sure all of your repositories are enabled by going to System>Administration>Software Sources.

---

### Post by rexxxlo on 2007-11-13
here is what happens with the first one


lolo@lolo-desktop:~$ sudo apt-get update
[sudo] password for lolo:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                     
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 5B in 1s (5B/s)  
Reading package lists... Done

and here is the second one ?


lolo@lolo-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for lolo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)


and all of the software sources _seem_ to be correct?

---

