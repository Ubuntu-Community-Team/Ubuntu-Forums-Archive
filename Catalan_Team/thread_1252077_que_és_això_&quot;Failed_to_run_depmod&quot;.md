---
title: "que és això? &quot;Failed to run depmod&quot;"
date: 2009-08-28
forum: Catalan Team
---

### Post by indiosincracia on 2009-08-28
Salut, recentment m'ha arribat una actualització del kernel, i ara l'a pe-te-get fa el ronso.
sabeu com resoldre el "Failed to run depmod"?
he fet:
sudo dpkg --configure -a
sudo apt-get -f instal
sense èxit.


nomagradaelbroquil@bullit-desktop:~$ sudo aptitude update
[sudo] password for nomagradaelbroquil:                 
Writing extended state information... Done  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_GB                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_GB                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_GB                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_GB                                   
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Release.gpg                                               
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Translation-en_GB                                         
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg [189B]                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_GB                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_GB                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_GB                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_GB                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_GB                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                                        
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release [49.6kB]                                     
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Release                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                                               
Ign [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                            
Hit [http://www.geekconnection.org](http://www.geekconnection.org) ubuntu/ Packages                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                                             
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages [160kB]                                
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]                          
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources [44.9kB]                                
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources [623B]                            
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages [54.0kB]                           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources [14.9kB]                            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages [6637B]                          
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources [2117B]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources                                    
Fetched 336kB in 6s (49.7kB/s)                                                                      
Reading package lists... Done                                                                       

Current status: 15 updates [+4].
nomagradaelbroquil@bullit-desktop:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done                                      
Building dependency tree                                           
Reading state information... Done                                  
Reading extended state information                                 
Initialising package states... Done                                
The following packages will be upgraded:                           
  app-install-data-commercial kdelibs-bin kdelibs5 kdelibs5-data libgl1-mesa-dri 
  libgl1-mesa-glx libglu1-mesa libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 
  libvorbis0a libvorbisenc2 libvorbisfile3 tzdata tzdata-java                          
The following partially installed packages will be configured:                         
  linux-image-2.6.28-15-generic                                                        
15 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.               
Need to get 3024kB/14.6MB of archives. After unpacking 16.4kB will be used.            
Do you want to continue? [Y/n/?] y                                                     
Writing extended state information... Done                                             
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libgl1-mesa-dri 7.4-0ubuntu3.2 [2728kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libgl1-mesa-glx 7.4-0ubuntu3.2 [114kB]          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libglu1-mesa 7.4-0ubuntu3.2 [179kB]             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe app-install-data-commercial 11.9.04.4 [2458B]                                                                                                   
Fetched 3024kB in 10s (278kB/s)                                                                     
Preconfiguring packages ...                                                                         
(Reading database ... dpkg: unrecoverable fatal error, aborting:                                    
 failed in buffer_read(fd): files list for package `linux-headers-2.6.28-15-generic': Input/output error                                                                                                
E: Sub-process /usr/bin/dpkg returned an error code (2)                                             
A package failed to install.  Trying to recover:                                                    
Setting up linux-image-2.6.28-15-generic (2.6.28-15.49) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.28-15-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done

Vinga merci!

---

### Post by papapep on 2009-08-28
*depmod* s'encarrega de gestionar les dependències entre moduls.
Jo esperaria un temps a veure que no sigui un problema concret del paquet aquest del nucli. A vegades passa, però en breu ho resolen.

També pots esborrar els .deb aquests en concret i tornar-los a descarregar, que no fos que t'haguessin quedat mal gravats (poc probable, però no impossible).

---

