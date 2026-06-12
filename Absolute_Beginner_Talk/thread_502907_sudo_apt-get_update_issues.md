---
title: "sudo apt-get update issues"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by aliov_85 on 2007-07-17
Hello every body,

I'm on feisty version and I think I made a mistake at the time of installing some packages of dapper by error.

when I do this command 
> sudo apt-get update

I got:
> Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]            
Get:2 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US    
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg                         
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_US                    
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_US    
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Translation-en_US           
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_US              
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages                       
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages                   
Get:5 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages                       
  404 Not Found
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages                   
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_US        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]              
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/multiverse Packages            
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Packages            
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6360B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_US          
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Packages                  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [49.4kB]       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Fetched 107kB in 33s (3152B/s)                                                 
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Can any one help please?

---

### Post by overdrank on 2007-07-17
> **aliov_85 said:**
> Hello every body,

I'm on feisty version and I think I made a mistake at the time of installing some packages of dapper by error.

when I do this command 


I got:


Can any one help please?

Hi you need to edit your apt list by this command
```
gksudo gedit /etc/apt/sources.list
```
And remove the dapper repos
Terminal is located under applications, accessories, terminal.

---

### Post by aliov_85 on 2007-07-17
Hello overdrank, thanks for your reply,

I did what you told me, but there is steel some problems remaining:

> 
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Do you have any idea?

thanks 
Ali

---

### Post by overdrank on 2007-07-17
> **aliov_85 said:**
> Hello overdrank, thanks for your reply,

I did what you told me, but there is steel some problems remaining:



Do you have any idea?

thanks 
Ali

Hi you can try to go to synaptic manager an fix broken package, under edit. then click reload. Then see if you get any errors in the terminal 
```
sudo apt-get update
```

---

### Post by aliov_85 on 2007-07-17
I went to synaptic,
and I did as you told, when I clicked on fix broken packages, and then clicked on reload, i got:
> 
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

