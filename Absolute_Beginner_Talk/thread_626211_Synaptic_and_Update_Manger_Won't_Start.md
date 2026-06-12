---
title: "Synaptic and Update Manger Won't Start"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by esc1 on 2007-11-28
I saw a few similar threads after searching, but they didn't really help me. I am still a Ubuntu novice.

I had been using a bzr version advant window navigator. The package was broken. Not sure why, but I had to uninstall whenever I wanted to update my system. I started to uninstall advant and looked away from screen. Looked back and package manager was closed.

Now synaptic and package manager won't start. They close as soon as popping on screen.

If I try to start synaptic from cl this is what it tells me:

Segmentation fault (core dumped)

My system has been a bit odd.  Some files became read only and the system locked. After reboot I could not get to the login screen. There was an error about 80% through file system check. Message said to run fsck manually. I did and got file system errors. Went through some steps. There were Y or N questions to connect nodes. I pressed Y to all. Not sure if this stuff is related. Files not read only anymore. Just before that one lockup.

---

### Post by Partyboi2 on 2007-11-28
What happens when you do:
```
sudo apt-get update
```
 and
```
sudo apt-get upgrade
```

---

### Post by esc1 on 2007-11-28
Update gives:

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources                      
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [26.9kB]                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  404 Not Found
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
  404 Not Found
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                          
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages  
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages
Hit [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages
Fetched 27.1kB in 2s (11.4kB/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Upgrade:

Reading package lists... Done
Segmentation fault (core dumped)

---

### Post by Partyboi2 on 2007-11-28
Can you post your sources.list please
```
cat /etc/apt/sources.list

```

---

### Post by esc1 on 2007-11-28
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

## Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

---

### Post by PmDematagoda on 2007-11-28
Open up your sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

And disable the entries highlighted:-

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
 # newer versions of the distribution.
 
 deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
 
 ## Major bug fix updates produced after the final release of the
 ## distribution.
 deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe
 
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team, and may not be under a free licence. Please satisfy yourself as to 
 ## your rights to use the software. Also, please note that software in 
 ## multiverse WILL NOT receive any review or updates from the Ubuntu
 ## security team.
 deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
 
 ## Uncomment the following two lines to add software from the 'backports'
 ## repository.
 ## N.B. software from this repository may not have been tested as
 ## extensively as that contained in the main release, although it includes
 ## newer versions of some applications which may provide useful features.
 ## Also, please note that software in backports WILL NOT receive any review
 ## or updates from the Ubuntu security team.
 # deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
 # deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
 
 deb http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
 deb http://security.ubuntu.com/ubuntu feisty-security universe
 deb-src http://security.ubuntu.com/ubuntu feisty-security universe
 deb http://security.ubuntu.com/ubuntu feisty-security multiverse
 deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
 
 ## Medibuntu - Ubuntu 7.04 "feisty fawn"
 ## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
 [COLOR="Red"]deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
 deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
 deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free[/COLOR]
 
 # Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
 # Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
 # built using latest available (working) sources from git/svn/cvs... 
 [COLOR="red"]deb http://download.tuxfamily.org/3v1deb feisty eyecandy
 deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy[/COLOR]
 # deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
 
[COLOR="red"] deb http://blognux.free.fr/debian unstable main[/COLOR]
 
 ## Avant Window Navigator
[COLOR="red"] deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
 deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator[/COLOR]
```

By typing # in front of them, after editing is complete, do:-

```
sudo apt-get update
```

And try using Synaptic again.

---

### Post by esc1 on 2007-11-28
Working now. Thanks.

I don't need the sources for medibuntu do I?

Will I still get compiz fusion updates without the eyecandy sources?

---

### Post by PmDematagoda on 2007-11-28
You can re-enable the eye-candy repositories to see if they do work, and do not worry about breaking the system as such things do not affect the entire OS, if the repositories do not work, simply disable them again and try and find another working server for Compiz-fusion.

And Medibuntu is not really necessary unless you want to install packages like libdvdcss2 or similar.

---

