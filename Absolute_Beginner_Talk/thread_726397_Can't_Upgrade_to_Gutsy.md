---
title: "Can't Upgrade to Gutsy"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Wudugast on 2008-03-16
I am still using Feisty Fawn at the moment and want to upgrade to Gutsy Gibbon. I downloaded the install CD ISO and burned it because the software repositories weren't working for the update manager. Nothing is working yet - not even the upgrade from CD option. Can anyone help? Is upgrading from Feisty no longer supported? I've checked my network connections and everything seems to be fine. Here's what I get when I try to upgrade: 

root@Travis:/home/travis# sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty Release.gpg                           
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/main Translation-en_US                
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/universe Translation-en_US            
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/restricted Translation-en_US          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/multiverse Translation-en_US          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates Release.gpg                   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/main Translation-en_US        
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/universe Translation-en_US    
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/restricted Translation-en_US  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security Release.gpg                  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/main Translation-en_US       
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/universe Translation-en_US   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/restricted Translation-en_US 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/multiverse Translation-en_US 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty Release                               
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates Release                       
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security Release                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                         
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US              
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US          
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/main Packages                         
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/universe Packages                     
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/restricted Packages                   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/multiverse Sources                    
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/main Sources                          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/universe Sources                      
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/restricted Sources                    
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/multiverse Packages                   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/main Packages                 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/universe Packages             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/restricted Packages           
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/main Sources                  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/universe Sources              
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/restricted Sources            
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/main Packages                
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/universe Packages            
Get:1 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release.gpg [307B]              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/restricted Packages          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/multiverse Sources           
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/main Sources                 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/universe Sources             
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release.gpg                       
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Translation-en_US            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Translation-en_US        
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/restricted Sources           
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/multiverse Packages          
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/main Packages                         
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/universe Packages                     
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/restricted Packages                   
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/multiverse Sources                    
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/main Sources                          
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/universe Sources                      
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/restricted Sources                    
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty/multiverse Packages                   
  404 Not Found
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_US             
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/main Packages                 
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/universe Packages             
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/restricted Packages           
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/main Sources                  
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/universe Sources              
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-updates/restricted Sources            
  404 Not Found
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release                           
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/main Packages                
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/universe Packages            
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/restricted Packages          
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/multiverse Sources           
  404 Not Found
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/main Sources                 
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/universe Sources             
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/restricted Sources           
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) feisty-security/multiverse Packages          
  404 Not Found
Get:2 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release [17.0kB]                
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                  
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                       
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US                   
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages                     
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages             
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                   
  404 Not Found
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  302 Found
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
  404 Not Found
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages                  
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                   
  302 Found
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages                 
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                 
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources             
  302 Found
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                      
  404 Not Found
Get:3 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages [9597B]
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages  
  404 Not Found
Fetched 26.9kB in 1s (15.6kB/s)
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  302 Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  302 Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@Travis:/home/travis# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by solar george on 2008-03-16
Follow instructions from
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Wudugast on 2008-03-16
I have tried to follow these instructions and they won't work. The bit about making the CD load the upgrade prompt if it doesn't appear automatically (and it doesn't) isn't working, and here's what happens when I try to upgrade via the update manager:

Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found


I've had the computer search for the best sever in the software sources manager, and it works. But everything stays the same. I can download normal software updates, but the Gutsy upgrade seems unavailable.

Any other help?

---

### Post by Oldsoldier2003 on 2008-03-16
> **Wudugast said:**
> I have tried to follow these instructions and they won't work. The bit about making the CD load the upgrade prompt if it doesn't appear automatically (and it doesn't) isn't working, and here's what happens when I try to upgrade via the update manager:

Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-updates/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found


I've had the computer search for the best sever in the software sources manager, and it works. But everything stays the same. I can download normal software updates, but the Gutsy upgrade seems unavailable.

Any other help?
sounds like your package listings are out of date
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Wudugast on 2008-03-16
I ran those commands again, and I'm still getting 404s and "failed to fetch" everywhere. Here it is again. It just isn't doing anything. Where have these packages gone? Should I keep trying different mirrors?


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@Travis:/home/travis# sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty Release.gpg [191B]                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                  
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_US                       
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_US                   
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                         
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_US              
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_US          
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/main Translation-en_US                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Get:2 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release.gpg [307B]              
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release.gpg             
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Translation-en_US  
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Translation-en_US        
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                             
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/universe Translation-en_US               
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_US             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper Release                           
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/restricted Translation-en_US             
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Get:3 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release [17.0kB]                
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/multiverse Translation-en_US             
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
  302 Found
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
  404 Not Found
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages                     
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages                 
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
  302 Found
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
  404 Not Found
Get:4 [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates Release.gpg [191B]             
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
  404 Not Found
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main Packages                     
  404 Not Found
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/main Translation-en_US           
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) dapper/main-all Packages                 
  404 Not Found
Get:5 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages [9597B]            
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/universe Translation-en_US       
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/restricted Translation-en_US
Get:6 [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security Release.gpg [191B]
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/main Translation-en_US
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/universe Translation-en_US
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/restricted Translation-en_US
Ign [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/multiverse Translation-en_US
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty Release           
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates Release                        
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security Release                       
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/main Packages                          
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/universe Packages 
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/restricted Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/multiverse Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/main Sources      
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/universe Sources  
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/restricted Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty/multiverse Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/main Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/universe Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/restricted Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/main Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/universe Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-updates/restricted Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/main Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/universe Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/restricted Packages
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/multiverse Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/main Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/universe Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/restricted Sources
Hit [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) feisty-security/multiverse Packages
Fetched 26.9kB in 5s (4822B/s)                          
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  302 Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/dapper/main-all/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@Travis:/home/travis# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Travis:/home/travis# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@Travis:/home/travis#

---

