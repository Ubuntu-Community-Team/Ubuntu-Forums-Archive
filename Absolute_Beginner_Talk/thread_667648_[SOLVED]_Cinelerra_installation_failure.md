---
title: "[SOLVED] Cinelerra installation failure"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by malty on 2008-01-14
Using the instructions in the Ubuntu Geeks howto guide for the installation of Cinelerra and using copy and paste to ensure accuracy I had the following in the terminal..........
john@john-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]      
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_GB           
Get: 6 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release.gpg [189B]                
Ign [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Get: 7 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB     
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release.gpg                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Translation-en_GB                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Get: 8 [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release [5535B]                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch/main Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB [2395B] 
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]  
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Get: 13 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                   
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                   
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                                      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages             
Ign [http://giss.tv](http://giss.tv) ./ Release.gpg                               
Ign [http://giss.tv](http://giss.tv) ./ Translation-en_GB   
Ign [http://giss.tv](http://giss.tv) ./ Release
Ign [http://giss.tv](http://giss.tv) ./ Packages
Ign [http://giss.tv](http://giss.tv) ./ Sources
Get: 14 [http://giss.tv](http://giss.tv) ./ Packages [3220B]
Get: 15 [http://giss.tv](http://giss.tv) ./ Sources [947B]      
Fetched 46.1kB in 3s (11.8kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
john@john-desktop:~$ sudo aptitude install Cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find package "Cinelerra".  However, the following
packages contain "Cinelerra" in their name:
  cinelerra 
The following packages are unused and will be REMOVED:
  libboost-python1.34.1 liblzo1 python-celementtree python-qt3 python-rpm 
  python-urlgrabber 
0 packages upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 24.5MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 153122 files and directories currently installed.)
Removing libboost-python1.34.1 ...
Removing liblzo1 ...
Removing python-celementtree ...
Removing python-qt3 ...
Removing python-rpm ...
Removing python-urlgrabber ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
john@john-desktop:~$ sudo gedit /etc/sysctl.conf
john@john-desktop:~$ sudo sysctl -p
kernel.printk = 4 4 1 7
kernel.maps_protect = 1
error: "Invalid argument" setting key "kernel.shmmax"

As far as I know I had copied everything, step by step as per the guide. The last entry is instead of a reboot ?
                                                               
 Any suggestions please ? 
                                                Regards
                                                                  Malty

---

### Post by Cypher on 2008-01-15
While following guides, please ALWAYS read the output before blindly following to the next step. You will notice that your "sudo aptitutde install Cinelerra" command failed because the package is called "cinelerra" instead.

So use "sudo aptitude install cinelerra" and then continue..

---

### Post by malty on 2008-01-15
Cypher,
             Thanks for the information, Cinelerra is now up and running.
Just one small point, however, I had punted about for what I had assumed was a reliable installation guide, coming as it did from again what I had assumed was a reliable source, I then used copy and paste to avoid typing errors. Obviously I have in future to assume these are only general guides and double check as I go.  Once again thanks for your help
                              Kind regards
                                                                Malty
PS....how do I add an official thanks to these posts ??

---

