---
title: "cant update jaunty ppc on ibook g4"
date: 2010-12-24
forum: Apple Hardware Users
---

### Post by cevin7 on 2010-12-24
Ok 

so after install several different versions of ubuntu on my ibook g4 I finally got xubuntu jaunty up and running. the problem is it wont update anything 

when i run sudo apt-get update it fails to fetch anything from the repos. also when i go to 
aplications software sources it wont let me check the important security updates tab at all.
I installed ubuntu hardy on my g4 powermac and that runs just fine but it doesn't work correctly on my ibook so i would really like to stick with jaunty but i cant seem to find a solution.

here is my sources.list

# deb cdrom:[Xubuntu 9.04 _Jaunty Jackalope_ - Release powerpc (20090423)]/ jaunty main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty main restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates main restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty multiverse
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates multiverse
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security restricted main
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security main restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-backports restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-updates main restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty main universe restricted multiverse
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty universe main multiverse restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security universe main multiverse restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-security universe main multiverse restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates universe main multiverse restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-updates universe main multiverse restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-proposed universe main multiverse restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-proposed universe main multiverse restricted
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-backports universe main multiverse restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) jaunty-backports universe main multiverse restricted

also is it possible that my authentication keys are wrong and if so where would i find the correct ones.

this is what i get when i run sudo apt-get update

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages          
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages                
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages          
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages            
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/main Packages                 
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security/restricted Packages           
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
  404 Not Found [IP: 91.189.88.31 80]
Fetched 3307kB in 11s (292kB/s)                                                
W: Failed to fetch [http://ports.ubuntu.com/dists/jaunty-security/restricted/binary-powerpc/Packages](http://ports.ubuntu.com/dists/jaunty-security/restricted/binary-powerpc/Packages)  404 Not Found

W: Failed to fetch [http://ports.ubuntu.com/dists/jaunty-security/main/binary-powerpc/Packages](http://ports.ubuntu.com/dists/jaunty-security/main/binary-powerpc/Packages)  404 Not Found

W: Failed to fetch [http://ports.ubuntu.com/dists/jaunty-security/universe/binary-powerpc/Packages](http://ports.ubuntu.com/dists/jaunty-security/universe/binary-powerpc/Packages)  404 Not Found

W: Failed to fetch [http://ports.ubuntu.com/dists/jaunty-security/multiverse/binary-powerpc/Packages](http://ports.ubuntu.com/dists/jaunty-security/multiverse/binary-powerpc/Packages)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-powerpc/Packages)  404 Not Found [IP: 91.189.88.31 80]

---

### Post by mikcarroll on 2010-12-29
**I've got the same problem with Jaunty, ppc G4 imac ,can't  mark security tab either, and google isn't producing any help. Must not be a well known fix yet. If I find it or figure it out I'll post it here. I saw on another board someone talking about using the repositories from kubuntu.Have you seen [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1084539") yet?I haven't tried**[COLOR=Gray][SIZE=5][FONT=Verdana]** making a repository dvd**[/FONT][/SIZE][/COLOR][FONT=Verdana][B][SIZE=5][COLOR=Gray]. [SIZE=1]Seems like an option though.I've used[ these]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1084539") before and just replaced the distro name on every line, it worked until I flubbed it again.

BTW, I'll post my output after an update to cross reference yours. I wonder if 9.10 fixes the problem? Of course getting the iso to one cd is a pain in the *** at 705mb.
[/SIZE] [/COLOR][/SIZE][/B][/FONT]

---

### Post by linuxopjemac on 2010-12-29
Why don't you guys install MintPPC ?

---

### Post by NightwishFan on 2010-12-29
Kubuntu and Ubuntu use the same repositories. Also, Jaunty is end of life. Perhaps this will help:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by mikcarroll on 2010-12-29
I found out that 9.10 will work on my imac so I'm just going to upgrade, but in order to upgrade I had to go software sources and delete all partners then reload and upgrade. My upgrade is downloading now so it seems as if deleting the partners worked for upgrading not sure  if it will fix updating..
lol my first message was a lot of cut n paste, looks like Frankenstein!!

---

### Post by mikcarroll on 2010-12-29
> **linuxopjemac said:**
> Why don't you guys install MintPPC ? 
Honestly,I have not checked out mint just because I don't like the name and I haven't heard anyone talking about it. I will check it out now though, thanks.

 I checked it out, there seems to be no community support yet, I also had to create an account just to view how to install, which is a  PIA. Never found a download page on their site either. Once they get their crap together I may check it out again but for now I'm sticking with Ubuntu.Mint seems like it's still Alpha, I'm not a tester.

---

### Post by NightwishFan on 2010-12-29
I do not use Mint either, but I am pretty sure it is not that bad.

Why not install ubuntu 10.04 with power pc? [http://cdimage.ubuntu.com/ports/releases/lucid/release/](http://cdimage.ubuntu.com/ports/releases/lucid/release/)

It is a LTS release and will be supported for 3 years. Edit: Well community support, as it is not official I am pretty sure. I think it will still be useful for 3 years.

---

