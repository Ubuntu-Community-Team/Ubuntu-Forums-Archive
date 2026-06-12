---
title: "update manager and synaptic"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-20
ok well im having a few problems.

1. I can't use synaptic package manager, every time i do i get this error message
```
E: Dynamic MMap ran out of room
E: Dynamic MMap ran out of room
E: Error occurred while processing libcupsimage2-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```
2. i can't use update manager, every time i get this error message
```
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Dynamic MMap ran out of room, E:Error occurred while processing libcupsimage2-dev (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

any clue on what to do for either one? 

Thanks Tennvolsmb

---

### Post by rocknrolf77 on 2007-07-20
First get a launchpad account and search for the bug. If it's not reported, or just a few times. Report it.

Have you added other repos?

---

### Post by alienexplorers on 2007-07-20
Try running in Terminal
> sudo apt-get update
then try
> sudo apt-get upgrade
See if you get the same errors or another.  Please report results here.

---

### Post by tennvolsmb on 2007-07-20
ok well for update i get this message 

```
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]                      
Ign http://archive.ubuntu.com dapper/main Translation-en_US                    
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]            
Ign http://security.ubuntu.com dapper-security/main Translation-en_US          
Ign http://security.ubuntu.com dapper-security/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Get:5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B] 
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com dapper/restricted Translation-en_US    
Ign http://archive.ubuntu.com dapper/universe Translation-en_US      
Ign http://archive.ubuntu.com dapper/multiverse Translation-en_US    
Get:6 http://archive.ubuntu.com dapper-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com dapper-updates/main Translation-en_US            
Ign http://archive.ubuntu.com dapper-updates/restricted Translation-en_US      
Ign http://security.ubuntu.com dapper-security/universe Translation-en_US      
Ign http://security.ubuntu.com dapper-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://security.ubuntu.com dapper-security Release                         
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Ign http://archive.ubuntu.com dapper-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com dapper-updates/multiverse Translation-en_US      
Get:7 http://archive.ubuntu.com dapper-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com dapper-backports/main Translation-en_US          
Ign http://archive.ubuntu.com dapper-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com dapper-backports/universe Translation-en_US      
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Ign http://archive.ubuntu.com dapper-backports/multiverse Translation-en_US    
Hit http://archive.ubuntu.com dapper Release                                   
Hit http://archive.ubuntu.com dapper-updates Release                           
Hit http://archive.ubuntu.com dapper-backports Release                         
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://security.ubuntu.com dapper-security/main Packages                   
Hit http://security.ubuntu.com dapper-security/restricted Packages             
Hit http://us.archive.ubuntu.com feisty/restricted Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages                      
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Ign http://packages.freecontrib.org dapper Release.gpg                         
Ign http://packages.freecontrib.org dapper/free Translation-en_US              
Hit http://us.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://archive.ubuntu.com dapper/main Packages                             
Hit http://archive.ubuntu.com dapper/restricted Packages                       
Hit http://archive.ubuntu.com dapper/universe Packages                         
Hit http://archive.ubuntu.com dapper/multiverse Packages                       
Hit http://archive.ubuntu.com dapper/main Sources                              
Hit http://security.ubuntu.com dapper-security/universe Packages               
Hit http://security.ubuntu.com dapper-security/multiverse Packages             
Hit http://security.ubuntu.com dapper-security/main Sources                    
Hit http://security.ubuntu.com dapper-security/restricted Sources              
Hit http://security.ubuntu.com dapper-security/universe Sources                
Hit http://security.ubuntu.com dapper-security/multiverse Sources              
Ign http://packages.freecontrib.org dapper/non-free Translation-en_US          
Ign http://packages.freecontrib.org dapper Release                   
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources   
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://packages.freecontrib.org dapper/free Packages
  404 Not Found
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://packages.freecontrib.org dapper/non-free Packages
  404 Not Found
Err http://packages.freecontrib.org dapper/free Sources
  404 Not Found
Err http://packages.freecontrib.org dapper/non-free Sources
  404 Not Found
Fetched 7B in 1s (5B/s)  
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz  404 Not Found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

and for upgrade i get 

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by alienexplorers on 2007-07-20
You did not have synaptic or update manager running when you ran the apt-get commands?

---

### Post by tennvolsmb on 2007-07-20
no neither of them were running when i ran the commands

---

