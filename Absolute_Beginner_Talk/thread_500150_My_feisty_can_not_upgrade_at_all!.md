---
title: "My feisty can not upgrade at all!"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by cbweixin on 2007-07-13
Hi There,

I met some trouble. I can not upgrade my fesity at all. below is the error inforamtion:

I use vmware, the ubuntu is inside it. are those error caused by the firewall?

wx@wx-ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages                      
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                       
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages                    
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources                     
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages            
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources                   
  302 Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources             
  302 Found [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  302 Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  302 Found [IP: 91.189.89.6 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  302 Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  302 Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Inxsible on 2007-07-13
Does this happen each time? Maybe the location of those packages changed or something.

---

### Post by cbweixin on 2007-07-13
yes, it happens every time when I want to update it. how to solve this problem.

---

### Post by mendingo84 on 2007-07-13
or maybe something is wrong with the servers where the repos are kept. this thing happened to the Romanian servers on Tuesday if i remember correctly. have some patience. it will be solved. i don't think there's anything wrong with your OS.

---

### Post by cbweixin on 2007-07-13
It seems that I should modify /etc/apt/sources.list , how to modify it? I'm just afraid that if I don't make correct changes, the whole system would messed up. so anybody can give any hint. thanks a lot.

---

### Post by mendingo84 on 2007-07-13
post a copy of ```
cat /etc/apt/sources.list
``` plz

---

### Post by cbweixin on 2007-07-13
here is my sources.list:



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

---

### Post by cbweixin on 2007-07-13
can any one give me some help about how to fix my sources.list. I think something wrong with it.

but I don't know how to modify it.

---

### Post by mendingo84 on 2007-07-13
i can't find anything wrong in there. i can notice that you used automatix though. is that right? :) 
i stick to the conclusion that there is a problem with the US repositories. don't bother to much, it will be solved soon. you will be able to update tomorrow most probably.

---

### Post by cbweixin on 2007-07-13
mendingo84,

thank you so much.

---

### Post by mendingo84 on 2007-07-13
here's my sources.list, just in case:
```

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty multiverse universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty multiverse universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

```

i didn't use automatix...

---

### Post by sailor2001 on 2007-07-13
check in synaptics to see what repository you have checked.....I just changed mine to USA and immediately received 22 up-dates

---

### Post by mgmiller on 2007-07-13
I was also having problems with the US repos lately and found a neat little utility buried in synaptic to find the best repos for you.  

1) Start synaptic package manager.
2)At the top of the window Click on Settings > Repositories.
3)On the Ubuntu Software tab Open the drop down list next to where it says "Download From:
4)Click on Other
5)Click "Select Best Server"
6) The system will look through and test all the repos and select the best one for you.  This may take some time.
7)When it's done, you will need to click the Reload button at the top left of Synaptic and then you should be good to go.

---

