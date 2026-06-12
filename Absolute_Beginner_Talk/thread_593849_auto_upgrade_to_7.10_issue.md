---
title: "auto upgrade to 7.10 issue"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-10-27
Anyone have an idea what this is telling me?


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found



Is there a package I am missing?:confused:

---

### Post by taurus on 2007-10-27
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those repos to comment them out.  Save it and then run

```
sudo apt-get update
```
Now, see if you can upgrade it to Gutsy.

---

### Post by LE CHARBON on 2007-10-27
Does not seem to be listed:



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

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by taurus on 2007-10-27
You need to remove these repos if you want to upgrade your Feisty to Gutsy.

```

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

```

---

### Post by LE CHARBON on 2007-10-27
Same result after commenting those out. Should I erase those completely?

---

### Post by LE CHARBON on 2007-10-27
Probably easier to load from CD. Not sure.

---

### Post by taurus on 2007-10-27
After commenting (removing) those lines at the end of /etc/apt/sources.list, did you remember to run

[code]sudo apt-get update[code]
first?

---

### Post by LE CHARBON on 2007-10-27
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

#AUTOMATIX REPOS START

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
#deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
#deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main



Then I ran sudo apt-get update

and received this:

weston@weston-desktop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources           
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources   
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
  404 Not Found
Fetched 3B in 1s (2B/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
weston@weston-desktop:~$ 

Then got this again:



Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found


Any more ideas??:)

---

### Post by icechen1 on 2007-10-27
try going to system>administration>Software sources and see if there is any line with medibuntu in it?

---

### Post by LE CHARBON on 2007-10-27
Got it, right in front of me. Upgrade a sucess. Thanks.:guitar:

---

