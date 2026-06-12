---
title: "Nothing can install"
date: 2012-11-12
forum: Apple Hardware Users
---

### Post by cyanidetaco on 2012-11-12
**Just installed 12.04 on a G4 eMac and absolutely nothing will install. When I do sudo apt-get update it says this** 
(not sure if I had to copy it all, but did it anyways.)

johnny@POSapple:~$ sudo apt-get update
```
[sudo] password for johnny: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise InRelease  
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports InRelease
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security InRelease                         
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed InRelease                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:1 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release.gpg [198 B]                      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release.gpg              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports Release.gpg                      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release.gpg                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed Release.gpg                       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release                                    
  
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates Release                            
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main powerpc Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security Release                           
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner powerpc Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main powerpc Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main powerpc Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted powerpc Packages        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe powerpc Packages          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse powerpc Packages        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main TranslationIndex              
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse TranslationIndex        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted TranslationIndex        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe TranslationIndex          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/main powerpc Packages  
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/restricted powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/universe powerpc Packages        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/multiverse powerpc Packages      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/main TranslationIndex            
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/multiverse TranslationIndex      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/restricted TranslationIndex      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/universe TranslationIndex        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted Sources                
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Sources                  
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse Sources                
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main powerpc Packages             
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted powerpc Packages       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe powerpc Packages         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse powerpc Packages       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main TranslationIndex             
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse TranslationIndex       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted TranslationIndex       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe TranslationIndex         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/restricted powerpc Packages       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/main powerpc Packages             
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/multiverse powerpc Packages       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/universe powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/main TranslationIndex             
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/multiverse TranslationIndex       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/restricted TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/universe TranslationIndex
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Translation-en_CA             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main powerpc Packages                     
  404  Not Found
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/main Translation-en                
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/multiverse Translation-en          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/restricted Translation-en          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Translation-en_CA         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-updates/universe Translation-en            
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/main Translation-en              
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/multiverse Translation-en        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/restricted Translation-en        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main powerpc Packages           
  404  Not Found
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-backports/universe Translation-en          
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/main Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA                    
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/multiverse Translation-en         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/restricted Translation-en
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-security/universe Translation-en 
Get:2 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/main Translation-en_CA [10.4 kB]
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/main Translation-en               
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/multiverse Translation-en         
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/restricted Translation-en         
Get:3 [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/universe Translation-en_CA [663 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) precise-proposed/universe Translation-en           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 11.3 kB in 3s (3,172 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ports.ubuntu.com](http://ports.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release](http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release)  


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/binary-powerpc/Packages](http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/binary-powerpc/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
```



**When I try to install something, it says this:**

johnny@POSapple:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras


**I am connected to the internet, otherwise I would not be able to post this.**

---

### Post by howefield on 2012-11-12
Thread moved to the "*Apple Users*" forum.

---

### Post by valroadie on 2012-11-12
Try this in terminal:

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

---

### Post by valroadie on 2012-11-12
For an alternative, what you'll want to do is delete the sources that are giving you problems:

sudo ls /etc/apt/sources.list.d

Locate the sources that are giving you problems, for example you noted: 

[http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/source/Sources)

You can also use apt to rid of them for example:

sudo add-apt-repository --remove ppa:The_PPA_Name/ppa

Also, you might want to open the Update Manager, click settings (bottom left) and check the sources tab. 

Hope this helps!

---

