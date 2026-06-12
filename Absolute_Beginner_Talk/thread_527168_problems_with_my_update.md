---
title: "problems with my update"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by seng1978 on 2007-08-16
i need help
when i type

sudo apt-get update  

this happens
seng-laptop:/etc$ sudo apt-get update
Get:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty Release                                
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates Release                        
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Packages                          
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Sources                           
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Sources             
Get:3 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release.gpg [189B]                        
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper/all Translation-en_US                       
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release                                     
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release                                     
  
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US              
Get:5 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release [13.8kB]                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release                                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper/all Packages                                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper/all Packages                                
  404 Not Found
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources         
Err [http://raof.dyndns.org](http://raof.dyndns.org) dapper Release.gpg                                  
  Could not connect to raof.dyndns.org:80 (213.169.251.35), connection timed out
Err [http://raof.dyndns.org](http://raof.dyndns.org) dapper/eyecandy Translation-en_US
 any suggestions?

---

### Post by Seisen on 2007-08-16
First is their a particular reason why you dapper repositories mixed in with your feisty repositories? Also this one won't open up for me either.

[http://raof.dyndns.org](http://raof.dyndns.org)

---

### Post by seng1978 on 2007-08-16
i dont know, im new a newbie, i thought drapper and feisty are the same thing lol

---

### Post by Hobo Joe on 2007-08-16
Paste your sources.list file:

```

sudo gedit /etc/apt/sources.list

```

---

### Post by Seisen on 2007-08-16
Dapper and Feisty are different versions of Ubuntu.

---

### Post by seng1978 on 2007-08-16
sudo gedit /etc/apt/sources.list results:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper all
deb [http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/) dapper eyecandy flash multimedia mythtv all
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by Seisen on 2007-08-16
Change this one ```
deb http://ubuntu.moshen.de/ dapper al
```l to

```
deb http://ubuntu.moshen.de/ feisty experimental eyecandy misc multimedia 
``` and delete this one since it appears to be down or you can comment it out add this[SIZE="5"] (#)[/SIZE] in front of the line so it looks like this

```
#deb http://raof.dyndns.org/falcon/ dapper eyecandy flash multimedia mythtv all
```

then ```
sudo apt-get update 
``` and then let us know if you still get the errors.

---

### Post by seng1978 on 2007-08-16
sudo apt-get update
Get:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty Release                                
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates Release                        
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Packages                          
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/main Sources                           
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/universe Sources             
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty/multiverse Sources           
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) feisty-updates/restricted Sources             
Get:3 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release.gpg [189B]                        
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental Translation-en_US            
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/eyecandy Translation-en_US
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/misc Translation-en_US
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/multimedia Translation-en_US
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release     
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release                          
  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:6 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release [14.1kB]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                       
Ign [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release                            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages              
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental Packages
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/eyecandy Packages
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/misc Packages
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/multimedia Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 14.3kB in 4s (3101B/s)
Reading package lists... Done
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: You may want to run apt-get update to correct these problems

---

### Post by Seisen on 2007-08-16
Just put this in the terminal it will add the missing GPG key.

```
wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
```

---

### Post by seng1978 on 2007-08-17
:):):):):):):):)
yeih yeih yeih
thank u so sos o so so much.
It finally works

thank u again

---

### Post by seng1978 on 2007-08-17
now i got a problem with my upgrade
this happens when i type sudo apt-get upgrade:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  compiz compiz-core compiz-gtk compiz-plugins
The following packages will be upgraded:
  freetype2-demos libcairo2 libdecoration0 libfreetype6 libfreetype6-dev
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil
  libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libxft2
  mono-common mono-gac mono-jit mono-runtime
23 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 15.0MB of archives.
After unpacking 71.7kB disk space will be freed.
Do you want to continue [Y/n]? y
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental freetype2-demos 2.3.3-0mlind1
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libfreetype6-dev 2.3.3-0mlind1
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libfreetype6 2.3.3-0mlind1
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libxft2 2.1.12-1+turner3
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libcairo2 1.4.2-0ubuntu1+turner2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/eyecandy libdecoration0 1:0.5.0-0ubuntu1
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental mono-runtime 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental mono-gac 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental mono-jit 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental mono-common 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-corlib1.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-cairo1.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-corlib2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono0 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-system2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-security2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-data-tds2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-sharpzip2.84-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-system-data2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-sqlite2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-system-web2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono-system1.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Err [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty/experimental libmono2.0-cil 1.2.3.1-1ubuntu2
  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/freetype2-demos_2.3.3-0mlind1_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/freetype2-demos_2.3.3-0mlind1_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6-dev_2.3.3-0mlind1_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6-dev_2.3.3-0mlind1_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6_2.3.3-0mlind1_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6_2.3.3-0mlind1_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libxft2_2.1.12-1+turner3_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libxft2_2.1.12-1+turner3_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2_1.4.2-0ubuntu1+turner2_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2_1.4.2-0ubuntu1+turner2_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/eyecandy/libdecoration0_0.5.0-0ubuntu1_amd64.deb](http://ubuntu.moshen.de/pool/feisty/eyecandy/libdecoration0_0.5.0-0ubuntu1_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/mono-runtime_1.2.3.1-1ubuntu2_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/mono-runtime_1.2.3.1-1ubuntu2_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/mono-gac_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/mono-gac_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/mono-jit_1.2.3.1-1ubuntu2_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/mono-jit_1.2.3.1-1ubuntu2_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/mono-common_1.2.3.1-1ubuntu2_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/mono-common_1.2.3.1-1ubuntu2_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-corlib1.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-corlib1.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-cairo1.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-cairo1.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-corlib2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-corlib2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono0_1.2.3.1-1ubuntu2_amd64.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono0_1.2.3.1-1ubuntu2_amd64.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-security2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-security2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-data-tds2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-data-tds2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-sharpzip2.84-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-sharpzip2.84-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system-data2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system-data2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-sqlite2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-sqlite2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system-web2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system-web2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system1.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono-system1.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://ubuntu.moshen.de/pool/feisty/experimental/libmono2.0-cil_1.2.3.1-1ubuntu2_all.deb](http://ubuntu.moshen.de/pool/feisty/experimental/libmono2.0-cil_1.2.3.1-1ubuntu2_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Seisen on 2007-08-17
Open up your source list and remove that this line 

```
deb http://ubuntu.moshen.de/ feisty experimental eyecandy misc multimedia
``` and then do a 

```
sudo apt-get update
sudo apt-get upgrade
```

I checked that repository and it apparantly is no longer works.

---

