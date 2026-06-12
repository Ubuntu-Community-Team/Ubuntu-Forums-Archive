---
title: "Repo problems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kenflipkick on 2007-04-24
Every time I try to update my sources list, there's a whole bunch of errors/repos that don't download, until it finally freezes in the middle of downloading one.

Has anyone had problems with this?  It comes from a fresh install of Feisty.

Thanks for any help!

---

### Post by taurus on 2007-04-24
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by kenflipkick on 2007-04-24
Here it is:

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

### Post by taurus on 2007-04-24
Can you post the complete output of this command from a terminal?

```
sudo aptitude update
```

---

### Post by kenflipkick on 2007-04-24
Get:1 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US               
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US             
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release [57.2kB]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [32.4kB]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                            
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages [14B]             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [14B]       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources [14B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources               
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources [14B] 
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [14B] 
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources [14B]  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7628B]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources                        
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources [1710B]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                  
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [2640B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages               
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [14B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources [1544B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources [14B]        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                 
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources [20B]             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources                      
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources [20B]       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources                
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources [63.5kB]             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                         
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [2443B]           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                      
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [20B]       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages                
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources [1447B]            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                       
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.6 80]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources [20B]        
58% [6 Packages bzip2 0]  


the last one is where it froze and wouldn't download any more.

---

### Post by kenflipkick on 2007-04-25
Any help at all?

---

