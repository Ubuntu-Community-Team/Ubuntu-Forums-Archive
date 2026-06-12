---
title: "Cant check a package in the software update"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-12-13
I'm trying to install an update, and for the past few times I've done it there's been one package that I can't check off. The package is libgl1-mesa-dri. I'm not sure what it is, but it just sits there saying it needs an update but never letting me update it. ](*,)

---

### Post by taurus on 2006-12-13
What happens if you run it from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Amablue on 2006-12-13
This is what happens:

```
alex@Shigeru:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://media.blutkind.org edgy Release.gpg [189B]
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US                  
Err http://compiz-mirror.lupine.me.uk edgy Release.gpg                          
  Could not resolve 'compiz-mirror.lupine.me.uk'
Get:2 http://www.beerorkid.com edgy Release.gpg [189B]                          
Hit http://media.blutkind.org edgy Release                                      
Ign http://media.blutkind.org edgy/main-edgy Packages                           
Get:3 http://www.getautomatix.com edgy Release.gpg [189B]                       
Ign http://www.getautomatix.com edgy/main Translation-en_US                     
Hit http://media.blutkind.org edgy/main-edgy Packages                           
Err http://compiz-mirror.lupine.me.uk edgy/main-edgy Translation-en_US          
  Could not resolve 'compiz-mirror.lupine.me.uk'
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US                   
Hit http://www.getautomatix.com edgy Release                                    
Ign http://wine.lowvoice.nl dapper Release.gpg                                  
Ign http://wine.lowvoice.nl dapper/main Translation-en_US                       
Get:4 http://archive.ubuntu.com edgy Release.gpg [191B]                         
Ign http://archive.ubuntu.com edgy/main Translation-en_US                       
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                 
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]         
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US       
Ign http://dl.google.com stable Release.gpg                                     
Get:6 http://ubuntu.beryl-project.org edgy Release.gpg [191B]                   
Ign http://ubuntu.beryl-project.org edgy/main-edgy Translation-en_US            
Get:7 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Hit http://www.getautomatix.com edgy/main Packages                              
Ign http://compiz-mirror.lupine.me.uk edgy Release                              
Hit http://www.beerorkid.com edgy Release                                       
Hit http://wine.lowvoice.nl dapper Release                                      
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                   
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                 
Get:8 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                 
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US               
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US         
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US           
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US         
Ign http://dl.google.com stable/non-free Translation-en_US                      
Hit http://archive.canonical.com dapper-commercial Release                      
Get:9 http://ubuntu.beryl-project.org edgy Release [4952B]                      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Hit http://security.ubuntu.com edgy-security Release                            
Ign http://www.beerorkid.com edgy/main-edgy Packages                            
Ign http://xgl.compiz.info dapper Release.gpg                                   
Ign http://xgl.compiz.info dapper/main Translation-en_US                        
Ign http://compiz-mirror.lupine.me.uk edgy/main-edgy Packages                   
Ign http://wine.lowvoice.nl dapper/main Packages                                
Get:10 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Hit http://dl.google.com stable Release                                         
Hit http://www.beerorkid.com edgy/main-edgy Packages                            
Ign http://ubuntu.beryl-project.org edgy Release                                
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Get:11 http://archive.ubuntu.com edgy-security Release.gpg [191B]               
Hit http://archive.canonical.com dapper-commercial/main Packages                
Hit http://security.ubuntu.com edgy-security/main Packages                      
Ign http://xgl.compiz.info dapper Release                                       
Err http://compiz-mirror.lupine.me.uk edgy/main-edgy Packages                   
  Could not resolve 'compiz-mirror.lupine.me.uk'
Hit http://dl.google.com stable/non-free Packages                               
Hit http://wine.lowvoice.nl dapper/main Packages                                
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US          
Ign http://ubuntu.beryl-project.org edgy/main-edgy Packages                     
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US        
Hit http://archive.ubuntu.com edgy Release                                      
Hit http://archive.ubuntu.com edgy-updates Release                              
Hit http://archive.ubuntu.com edgy-backports Release                            
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Ign http://xgl.compiz.info dapper/main Packages                                 
Err http://ubuntu.beryl-project.org edgy/main-edgy Packages                     
  404 Not Found [IP: 89.200.136.91 80]
Hit http://archive.ubuntu.com edgy-security Release                             
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Sources                 
Err http://xgl.compiz.info dapper/main Packages                                 
  404 Not Found
Hit http://archive.ubuntu.com edgy/main Packages                                
Hit http://archive.ubuntu.com edgy/restricted Packages     
Hit http://archive.ubuntu.com edgy/universe Packages       
Hit http://archive.ubuntu.com edgy/multiverse Packages     
Hit http://archive.ubuntu.com edgy/main Sources            
Hit http://archive.ubuntu.com edgy/restricted Sources      
Hit http://archive.ubuntu.com edgy/universe Sources        
Hit http://archive.ubuntu.com edgy/multiverse Sources      
Hit http://archive.ubuntu.com edgy-updates/main Packages   
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources    
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-updates/universe Sources
Hit http://archive.ubuntu.com edgy-updates/multiverse Sources
Err http://ubuntu.compiz.net edgy Release.gpg              
  Could not resolve 'ubuntu.compiz.net'
Hit http://archive.ubuntu.com edgy-backports/main Packages 
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Sources  
Hit http://archive.ubuntu.com edgy-backports/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/universe Sources
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources
Hit http://archive.ubuntu.com edgy-security/main Packages  
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Err http://ubuntu.compiz.net edgy/main-edgy Translation-en_US
  Could not resolve 'ubuntu.compiz.net'
Ign http://ubuntu.compiz.net edgy Release
Ign http://ubuntu.compiz.net edgy/main-edgy Packages
Err http://ubuntu.compiz.net edgy/main-edgy Packages
  Could not resolve 'ubuntu.compiz.net'
Fetched 5340B in 5s (1059B/s)        
Reading package lists... Done
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
alex@Shigeru:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  libgl1-mesa-dri 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
alex@Shigeru:~$ 

```

---

### Post by taurus on 2006-12-13
Looks like you have a few broken repos in your /etc/apt/sources.list!!!  Paste your /etc/apt/sources.list here then...

```
cat /etc/apt/sources.list
```

---

### Post by Amablue on 2006-12-13
Yeah, I realized that after I posted it. 

I never use Beryl on my computer anyway since it's too unstable, so I went ahead a removed all the repos and it seems to have fixed itself.

---

### Post by tedrogers on 2006-12-13
I have a similar issue with a GPG error, but this only manifested itself after I installed Automatix2.

The actual error is as follows:

```
W: GPG error: http://archive.ubuntu.com edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

Here's the output of my sudo aptitude update:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 http://www.getautomatix.com edgy Release.gpg [189B]
Get:2 http://archive.ubuntu.com edgy-backports Release.gpg [191B]                                                            
Get:3 http://security.ubuntu.com edgy-security Release.gpg [191B]                                                            
Ign http://security.ubuntu.com edgy-security/main Translation-en_GB                                              
Get:4 http://gb.archive.ubuntu.com edgy Release.gpg [191B]                                                       
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_GB                                        
Ign http://security.ubuntu.com edgy-security/universe Translation-en_GB                                          
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_GB                                        
Hit http://security.ubuntu.com edgy-security Release                                                             
Ign http://www.getautomatix.com edgy/main Translation-en_GB                                
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]                    
Ign http://archive.canonical.com dapper-commercial/main Translation-en_GB                  
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB                        
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB                                       
Hit http://archive.canonical.com dapper-commercial Release                                                      
Ign http://gb.archive.ubuntu.com edgy/main Translation-en_GB                              
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB                   
Ign http://gb.archive.ubuntu.com edgy/restricted Translation-en_GB                        
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB
Get:6 http://archive.ubuntu.com edgy-security Release.gpg [191B]    
Ign http://gb.archive.ubuntu.com edgy/universe Translation-en_GB                          
Ign http://archive.ubuntu.com edgy-security/main Translation-en_GB                        
Ign http://gb.archive.ubuntu.com edgy/multiverse Translation-en_GB  
Get:7 http://gb.archive.ubuntu.com edgy-updates Release.gpg [191B]   
Ign http://gb.archive.ubuntu.com edgy-updates/main Translation-en_GB 
Hit http://www.getautomatix.com edgy Release                         
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_GB
Hit http://security.ubuntu.com edgy-security/main Packages                                                     
Hit http://archive.canonical.com dapper-commercial/main Packages                                               
Ign http://gb.archive.ubuntu.com edgy-updates/restricted Translation-en_GB               
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_GB                 
Hit http://archive.ubuntu.com edgy-backports Release                                     
Ign http://gb.archive.ubuntu.com edgy-updates/universe Translation-en_GB                 
Hit http://security.ubuntu.com edgy-security/restricted Packages                         
Hit http://security.ubuntu.com edgy-security/universe Packages                           
Hit http://security.ubuntu.com edgy-security/multiverse Packages                         
Ign http://gb.archive.ubuntu.com edgy-updates/multiverse Translation-en_GB               
Hit http://gb.archive.ubuntu.com edgy Release                                            
Hit http://gb.archive.ubuntu.com edgy-updates Release                                    
Hit http://security.ubuntu.com edgy-security/main Sources                                
Hit http://security.ubuntu.com edgy-security/restricted Sources    
Hit http://security.ubuntu.com edgy-security/universe Sources      
Hit http://security.ubuntu.com edgy-security/multiverse Sources    
Hit http://archive.ubuntu.com edgy-security Release                
Hit http://www.getautomatix.com edgy/main Packages
Hit http://archive.ubuntu.com edgy-backports/main Packages          
Hit http://gb.archive.ubuntu.com edgy/main Packages                 
Hit http://gb.archive.ubuntu.com edgy/restricted Packages
Hit http://gb.archive.ubuntu.com edgy/universe Packages             
Hit http://archive.ubuntu.com edgy-backports/restricted Packages    
Hit http://archive.ubuntu.com edgy-backports/universe Packages      
Hit http://gb.archive.ubuntu.com edgy/multiverse Packages           
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages    
Hit http://gb.archive.ubuntu.com edgy/main Sources                  
Hit http://gb.archive.ubuntu.com edgy/restricted Sources
Hit http://gb.archive.ubuntu.com edgy/universe Sources
Hit http://gb.archive.ubuntu.com edgy/multiverse Sources
Err http://archive.ubuntu.com edgy-security Release
  
Get:8 http://archive.ubuntu.com edgy-security Release [30.9kB]
Hit http://gb.archive.ubuntu.com edgy-updates/main Packages
Ign http://archive.ubuntu.com edgy-security Release       
Hit http://gb.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://gb.archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages
Hit http://gb.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com edgy-updates/main Sources
Hit http://gb.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy-security/multiverse Packages
Hit http://gb.archive.ubuntu.com edgy-updates/universe Sources
Hit http://gb.archive.ubuntu.com edgy-updates/multiverse Sources
Fetched 31.1kB in 5s (5932B/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Also here's the output of cat /etc/apt/sources.list:

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

Doing a apt-get update does not fix the problem.

Any ideas?

Thanks in advance.

---

### Post by taurus on 2006-12-13
Here's your new /etc/apt/sources.list...

```

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricte universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://www.getautomatix.com/apt edgy main

```
Then,

```
sudo aptitude remove automatix2
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install automatix2
```

---

### Post by tedrogers on 2006-12-14
Thanks for doing that...but what was the problem. Did I have duplicates or old repos in there? Thanks.

---

### Post by taurus on 2006-12-14
No.  You just have to enable both universe & multiverse repos (by removing the # sign in front of them).

---

