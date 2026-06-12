---
title: "ultimate repo"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by alnhntr29 on 2007-09-04
Could someone tell me why I get a no data response when i try to add the ubuntu ultimate repo?
Something i am doing, or a problem with the repo?

---

### Post by MenZa on 2007-09-04
Have you updated? *sudo aptitude update*

---

### Post by alnhntr29 on 2007-09-04
This is what I get when i update.


billy@billy-desktop:~$ sudo aptitude update
Password:
Get:1 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release.gpg
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US           
Get:4 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_US               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US
Get:7 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                    
Get:10 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               
98% [Release gpgv 38406] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages              
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Fetched 7398B in 2s (3698B/s)
Reading package lists... Done
W: GPG error: [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: You may want to run apt-get update to correct these problems
billy@billy-desktop:~$

---

