---
title: "have a problum with the repo,s"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by nosfed438 on 2007-08-29
this is what i get 

Fetched 7401B in 1s (7136B/s)
Failed to fetch [http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2](http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


help!!!!!

---

### Post by davidjmayo on 2007-08-29
> **nosfed438 said:**
> this is what i get 

Fetched 7401B in 1s (7136B/s)
Failed to fetch [http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2](http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
**W: You may want to run apt-get update to correct these problems**
E: Some index files failed to download, they have been ignored, or old ones used instead.


help!!!!!

In a terminal  run 
```
sudo apt-get update
```

---

### Post by nosfed438 on 2007-08-29
i got the same thing 


Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:3 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release.gpg                        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Get:7 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
99% [7 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:8 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release                            
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US 
Get:12 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages            
98% [12 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages                         
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Fetched 7401B in 1s (6356B/s)
Failed to fetch [http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2](http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
me@me-desktop:~$

---

### Post by davidjmayo on 2007-08-29
> Failed to fetch [http://repoubuntusoftware.info/dists...6/Packages.bz2](http://repoubuntusoftware.info/dists...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
me@me-desktop:~$


Now I have some idea but I don't use ubuntu ultimate
Try looking at
[http://repoubuntusoftware.info/](http://repoubuntusoftware.info/)

---

