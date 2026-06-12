---
title: "Repository Update Problem"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-12-31
I just added the repo of qbittorrent and now when i run, i get this:
It halts on the 99% of gzip, for years, i waited for 30 solid minutes to get it done, tried it twice, even checked the connection, changed the servers to global and local, no use...
```

shoaibi@eagles-nest:~$ sagu
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:2 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://download.tuxfamily.org ubuntu Release.gpg [189B]                  
Ign http://download.tuxfamily.org ubuntu/bluetooth Translation-en_US           
Ign http://hydr0g3n.free.fr ./ Release.gpg                                     
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:5 http://us.archive.ubuntu.com gutsy-updates Release.gpg [187B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://download.tuxfamily.org ubuntu Release                               
Get:6 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Get:7 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]          
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Hit http://packages.medibuntu.org gutsy Release                                
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://download.tuxfamily.org ubuntu/bluetooth Packages                    
Hit http://archive.canonical.com gutsy Release                                 
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy-backports Release                       
Ign http://packages.medibuntu.org gutsy/free Packages                          
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://download.tuxfamily.org ubuntu/bluetooth Packages                    
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://us.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://us.archive.ubuntu.com gutsy/main Sources                            
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://packages.medibuntu.org gutsy/free Packages
Ign http://hydr0g3n.free.fr ./ Translation-en_US
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources       
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources         
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Ign http://hydr0g3n.free.fr ./ Release
Ign http://hydr0g3n.free.fr ./ Packages             
Ign http://hydr0g3n.free.fr ./ Sources                                         
Get:8 http://hydr0g3n.free.fr ./ Packages                                      
Get:9 http://hydr0g3n.free.fr ./ Sources [3178B]                               
99% [8 Packages gzip 0]                                                        
[1]+  Stopped                 sudo apt-get update
shoaibi@eagles-nest:~$ sagu
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
shoaibi@eagles-nest:~$ sudo rm -rf /var/lib/apt/lists/lock 
shoaibi@eagles-nest:~$ sagi qbittorent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qbittorent
shoaibi@eagles-nest:~$ sagi qbittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qbittorrent
shoaibi@eagles-nest:~$ sagu
Get:1 http://download.tuxfamily.org ubuntu Release.gpg [189B]                  
Ign http://download.tuxfamily.org ubuntu/bluetooth Translation-en_US           
Get:2 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://hydr0g3n.free.fr ./ Release.gpg                                     
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:5 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Hit http://download.tuxfamily.org ubuntu Release                               
Hit http://archive.canonical.com gutsy Release                                 
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:6 http://us.archive.ubuntu.com gutsy-updates Release.gpg [187B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://download.tuxfamily.org ubuntu/bluetooth Packages                    
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Get:7 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]          
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US    
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://download.tuxfamily.org ubuntu/bluetooth Packages                    
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources     
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy-backports Release                       
Ign http://hydr0g3n.free.fr ./ Translation-en_US                               
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://packages.medibuntu.org gutsy Release
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources                 
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources                    
Ign http://packages.medibuntu.org gutsy/free Packages                          
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources              
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages          
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Ign http://hydr0g3n.free.fr ./ Release                               
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages       
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Ign http://hydr0g3n.free.fr ./ Packages             
Ign http://hydr0g3n.free.fr ./ Sources                                         
Get:8 http://hydr0g3n.free.fr ./ Packages                                      
Get:9 http://hydr0g3n.free.fr ./ Sources [3178B]                               
99% [8 Packages gzip 0]  

```



My sources:
```

shoaibi@eagles-nest:~$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free

#Repository for Blueman
deb http://download.tuxfamily.org/blueman ubuntu bluetooth

#for qBittorent
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./


```

---

### Post by Perfect Storm on 2007-12-31
I think the error is none of yours but the source you added. Better contact the owner. (note there's always a security risk to add unofficial sources).

---

### Post by Sef on 2007-12-31
> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
shoaibi@eagles-nest:~$ sudo rm -rf /var/lib/apt/lists/lock 
shoaibi@eagles-nest:~$ sagi qbittorent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qbittorent
shoaibi@eagles-nest:~$ sagi qbittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qbittorrent

Comment out qtorrent.  To comment it out put a # at the start of the line.

So instead of this: ```
#for qBittorent
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
```

You have this: ```
#for qBittorent
#deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
#deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
```

---

### Post by SOULRiDER on 2007-12-31
Also, the site seems to be no more, thats why the package list won't download.

---

