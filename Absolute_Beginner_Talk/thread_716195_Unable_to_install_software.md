---
title: "Unable to install software"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by thischarmingman on 2008-03-05
Hi

I've had many many problems since I installed iTunes 7 on wine. Basically software will not install, applets have disappeared resulting in errors and the add/remove software has gone also. This is what happened when i tried to install banshee

[I]david@david-laptop:~$ sudo apt-get install banshee
[sudo] password for david:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libnjb5 but it is not installable
           Depends: libmono-cairo2.0-cil (>= 1.0) but it is not installable
           Depends: libmono1.0-cil (>= 1.2.4) but it is not installable
           Depends: gstreamer0.10-plugins-base but it is not installable
           Depends: gstreamer0.10-plugins-good (>= 0.10.6) but it is not installable
           Depends: gstreamer0.10-gnomevfs but it is not installable
E: Broken packages
david@david-laptop:~$ [/I]

Its a similar situation for other applications. I have removed itunes and reinstalled wine, but still have the same problems. Really need help on this one.

Thanks

---

### Post by spiderbatdad on 2008-03-05
```
sudo dpkg --purge -a
sudo apt-get update
```

Try running that and post back any errors.

---

### Post by thischarmingman on 2008-03-05
david@david-laptop:~$ sudo dpkg --purge -a
david@david-laptop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Translation-en_IE          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Translation-en_IE                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Translation-en_IE    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Translation-en_IE      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Translation-en_IE                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Translation-en_IE              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Translation-en_IE              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Translation-en_IE            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Translation-en_IE      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
Get:1 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]                             
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Translation-en_IE                       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IE               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IE                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources              
Hit [http://deb.opera.com](http://deb.opera.com) etch Release                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources                
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
  404 Not Found
Err [http://deb.opera.com](http://deb.opera.com) etch Release                                          
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages             
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                    
  404 Not Found
Get:3 [http://deb.opera.com](http://deb.opera.com) etch Release [866B]                                 
Ign [http://deb.opera.com](http://deb.opera.com) etch Release                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources                      
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources              
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages               
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources                
  404 Not Found
Get:4 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg                                     
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources                              
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources                        
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources                          
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages                         
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages                             
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages                       
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                       
  404 Not Found [IP: 91.189.88.46 80]
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages                                
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages                     
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages               
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources                      
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources                
  404 Not Found [IP: 91.189.88.46 80]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg                                       
Get:5 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Translation-en_IE                          
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Translation-en_IE                      
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release.gpg                          
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Translation-en_IE               
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Translation-en_IE           
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Translation-en_IE                            
Get:6 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Translation-en_IE                      
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Translation-en_IE                        
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release                                
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release                              
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release                                         
Get:8 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_IE               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                              
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release                                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources               
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages                               
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages       
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages                             
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages                             
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages                                 
Ign [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages                    
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages
  302 Found [IP: 203.16.234.90 80]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:13 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Err [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages
  302 Found [IP: 203.16.234.90 80]
Get:14 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:15 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:16 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Err [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 1057B in 3s (270B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  302 Found [IP: 203.16.234.90 80]
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  302 Found [IP: 203.16.234.90 80]
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
david@david-laptop:~$ sudo dpkg --purge -a
david@david-laptop:~$ sudo apt-get update

---

