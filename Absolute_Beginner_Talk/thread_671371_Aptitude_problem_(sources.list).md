---
title: "Aptitude problem (sources.list)"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by S1acker on 2008-01-18
I live in Malaysia and our internet is not very good. I was getting 10kbps when downloading stuff with apt-get. I went and edited /etc/apt/sources.list and replaced all of the my. to sg. which is Singapore. I can normally max my connection their (100kbps).

Anyway I think I've mucked some stuff up;

```
graham@linux:~$ sudo apt-get update
Err http: feisty Release.gpg
  Unable to connect to  http:
Ign http: feisty Release                                                    
Ign http: feisty/main Sources                                               
Ign http: feisty/restricted Sources                                         
Err http: feisty/main Sources                                               
  Unable to connect to  http:
Err http: feisty/restricted Sources                                         
  Unable to connect to  http:
Get:1 http://sg.archive.ubuntu.com feisty Release.gpg [191B]                
Ign http://sg.archive.ubuntu.com feisty/main Translation-en_US
Ign http://sg.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://sg.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://sg.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:2 http://sg.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://sg.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://sg.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://sg.archive.ubuntu.com feisty Release                                
Hit http://sg.archive.ubuntu.com feisty-updates Release                        
Hit http://sg.archive.ubuntu.com feisty/main Packages                          
Hit http://sg.archive.ubuntu.com feisty/restricted Packages                    
Hit http://sg.archive.ubuntu.com feisty/universe Packages                      
Hit http://sg.archive.ubuntu.com feisty/universe Sources                       
Hit http://sg.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://sg.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://sg.archive.ubuntu.com feisty-updates/main Packages                  
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://sg.archive.ubuntu.com feisty-updates/main Sources                   
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Hit http://sg.archive.ubuntu.com feisty-updates/restricted Sources             
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Fetched 3B in 14s (0B/s)                                                       
Failed to fetch http:/sg.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Unable to connect to  http:
Failed to fetch http:/sg.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  Unable to connect to  http:
Failed to fetch http:/sg.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  Unable to connect to  http:
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

sources.list

```
graham@linux:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sg.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http:/sg.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sg.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://sg.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sg.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://sg.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sg.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://sg.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://sg.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

please help.

---

### Post by gn2 on 2008-01-18
Open Synaptic Package Manager, Settings>Repositories>Ubuntu Software>Download From>Other and choose which one you want from the list.

---

### Post by S1acker on 2008-01-18
that should fix all my problems ? if so thanks

---

### Post by gn2 on 2008-01-18
> **S1acker said:**
> that should fix all my problems ? 

Should do, hopefully :)

---

