---
title: "Update Issue"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Begemot74 on 2008-02-22
Hi,



I'm having problems updating my system (7.10) - for the past week or so, whenever i try to do so, i get an error message saying archive.ubuntu.com is uncontactable. Internet connectivity is fine otherwise. When I first installed Ubuntu, update worked fine, and I'm not aware of having made any changes that would cause this issue. Does anyone have any suggestions for me, please?

---

### Post by billgoldberg on 2008-02-22
Open up synaptic package manager (system -> administration) and go to setting -> repositories.

Verify that the repo's are selected.

Then press the reload button in synaptic.

---------------------

You can't update if you have synaptic or add/remove open.

---------------------

Highly unlikable but you didn't block archives.ubuntu.com in /etc/hosts did you?

---------------------

If you still have the ubuntu cd in the tray, remove it and then try updating.

---------------------

Try "sudo apt-get update"  (without the " ") in the terminal (applications -< accessories). If you can't upload via the update manager this most likely won't work either, but you never know.

---

### Post by Begemot74 on 2008-02-22
Thanks for the swift reply, Bill. I'll give it a go, and let you know.

---

### Post by Begemot74 on 2008-02-22
Had a look  in Synaptic - everything looked ok. Tried updating from the Terminal, and got the following:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not resolve ‘archive.canonical.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not resolve ‘archive.ubuntu.com’
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not resolve ‘security.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
  Could not resolve ‘archive.canonical.com’
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
  Could not resolve ‘security.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
  Could not resolve ‘archive.ubuntu.com’
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
  Could not resolve ‘security.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
  Could not resolve ‘archive.ubuntu.com’
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
  Could not resolve ‘security.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
  Could not resolve ‘archive.ubuntu.com’
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
  Could not resolve ‘security.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg                       
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
  Could not resolve ‘archive.canonical.com’
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
  Could not resolve ‘archive.canonical.com’
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB  
  Could not resolve ‘archive.ubuntu.com’
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages               
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB        
  Could not resolve ‘archive.ubuntu.com’
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB  
  Could not resolve ‘archive.ubuntu.com’
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB    
  Could not resolve ‘archive.ubuntu.com’
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages         
  Could not resolve ‘security.ubuntu.com’
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages               
  Could not resolve ‘security.ubuntu.com’
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages         
  Could not resolve ‘security.ubuntu.com’
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages           
  Could not resolve ‘security.ubuntu.com’
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not resolve ‘archive.ubuntu.com’
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve ‘archive.canonical.com’
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.canonical.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  Could not resolve ‘archive.canonical.com’
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  Could not resolve ‘archive.canonical.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  Could not resolve ‘security.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve ‘archive.ubuntu.com’
Reading package lists... Done
E: Some index files failed t?o download, they have been ignored, or old ones used instead.

So, what am I doing wrong?

---

### Post by taurus on 2008-02-22
You can either go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and select another mirror site or the main server.  Then, close it and click Refresh.  Now see if you can update your machine. 

Or post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Begemot74 on 2008-02-22
Bill, 

in response to your question about blocking archives.ubuntu.com in etc/hosts, no I didn't. Where will i find the hosts file in Ubuntu, by the way?

Thanks for any assistance you're able to offer.

---

### Post by thewaffler20 on 2008-02-22
I am getting a similar error as well when trying to do a fresh install of Gutsy. I have tried 64bit and 32bit and am still getting the same error when i try to enable the Repos and then update. 

When using the software sources prompt after clicking the repos and trying to refresh it i get an error and have to force quit. When I open the detail section I get "Hit" and "Failed" by some of the Repos. 

I have tried this both wirelessly and wired. Also can browse the internet fine and if i throw a repo into firefox i can start downloading from there. 

Rather confused since i have installed Gutsy on this computer twice before this. 

Third time i know...i tried installing Hardy and had some issues. : )

---

### Post by taurus on 2008-02-22
> **thewaffler20 said:**
> I am getting a similar error as well when trying to do a fresh install of Gutsy. I have tried 64bit and 32bit and am still getting the same error when i try to enable the Repos and then update. 

When using the software sources prompt after clicking the repos and trying to refresh it i get an error and have to force quit. When I open the detail section I get "Hit" and "Failed" by some of the Repos. 

I have tried this both wirelessly and wired. Also can browse the internet fine and if i throw a repo into firefox i can start downloading from there. 

Rather confused since i have installed Gutsy on this computer twice before this. 

Third time i know...i tried installing Hardy and had some issues. : )

Wanna post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by thewaffler20 on 2008-02-22
> **taurus said:**
> Wanna post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

Welllllll.....i would but i am currently at work. might be able to hop on over lunch.

---

### Post by Begemot74 on 2008-02-22
[QUOTE=taurus;4381878]You can either go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and select another mirror site or the main server.  

[COLOR="Blue"]I've already tried this, unfortunately. Which ever server I choose, I get the same result.[/COLOR]

Then, close it and click Refresh.  Now see if you can update your machine. 

Or post your /etc/apt/sources.list.

[COLOR="Blue"]Here's the list:[/COLOR]


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Any ideas what could be wrong? Is there a possibility I've been hacked?

---

### Post by taurus on 2008-02-22
> **Begemot74 said:**
> 

[COLOR="Blue"]I've already tried this, unfortunately. Which ever server I choose, I get the same result.[/COLOR]

Then, close it and click Refresh.  Now see if you can update your machine. 

Or post your /etc/apt/sources.list.

[COLOR="Blue"]Here's the list:[/COLOR]


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Any ideas what could be wrong? Is there a possibility I've been hacked?

Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit editing window.  

Now, what happens when you run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by seventhc on 2008-02-22
Open it with gedit
```

gksu gedit /etc/apt/sources.list
``````

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

 
  deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

  deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

  deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

  deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

  deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

  deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

  deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

  deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

  deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse

 deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse

 deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

 deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner


 deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

 deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

 deb http://security.ubuntu.com/ubuntu gutsy-security universe

 deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

 deb http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```then
```

sudp apt-get update
```and try again, all I did was uncomment the lines, since I'm not sure when that happened.

**Edit**: never mind, above post is probably better.

---

### Post by seventhc on 2008-02-22
yikes, I didn't even notice the cd rom drive in the list....:(

---

### Post by thewaffler20 on 2008-02-22
When i went home at lunch my sources list was much like Begemonts....I didnt have the CD Rom uncommented but still needed to uncomment the other deb and deb-src. 

When i ran sudo apt-get update and get-upgrade i initially got a similar error to before. It would look up the repos in the terminal and then give [Hit] before some of them and then it would hang at 99%....cant remember what exactly it said....then I basically had to close terminal. 

Then somehow i kept trying it and it eventually advised me to try get-upgrade and then get-update.


Now my computer is currently downloading all the Upgrades/Updates...hopefully without any problems. (at work again)

Does this seem a little odd.

---

### Post by seventhc on 2008-02-22
oddities and computers are something to get used to...if it works, well, mark this thread as solved....No I can't explain it, but I've seen stranger things happen. Maybe someone else can explain. :)

---

### Post by Begemot74 on 2008-02-25
Taurus,

I tried what you suggested, but it doesn't seem to have changed anything, unfortunately. This is what I got when I tried to update:

Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy Release.gpg                              
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg                             
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not resolve &#8216;archive.canonical.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/restricted Translation-en_GB             
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB                  
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
  Could not resolve &#8216;archive.canonical.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Translation-en_GB                   
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Translation-en_GB               
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB              
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/multiverse Translation-en_GB             
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security Release.gpg                     
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
  Could not resolve &#8216;archive.canonical.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg                     
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates Release.gpg                      
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
  Could not resolve &#8216;archive.canonical.com&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Translation-en_GB     
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Translation-en_GB           
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/multiverse Translation-en_GB     
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Translation-en_GB       
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources               
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release.gpg                   
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy Release                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security Release                         
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Translation-en_GB        
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates Release                          
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB  
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/restricted Packages                      
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB    
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Packages                            
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB  
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                   
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/multiverse Packages                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/restricted Sources                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Sources                             
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release                       
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/multiverse Sources                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Sources                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/restricted Sources              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                            
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/main Sources                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources                      
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/multiverse Sources              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                       
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/universe Sources                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages                     
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Packages              
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Packages                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/multiverse Packages              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages                   
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Sources               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources                    
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Sources                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources              
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/multiverse Sources               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages               
Ign [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/restricted Packages                      
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Packages                            
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Packages                        
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Packages                 
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/multiverse Packages                      
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Packages           
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/restricted Sources                       
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Packages             
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/main Sources                             
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Packages           
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/multiverse Sources                       
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Sources                  
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy/universe Sources                         
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Sources            
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/restricted Sources              
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Sources              
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/main Sources                    
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Sources            
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/multiverse Sources              
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-security/universe Sources                
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Packages              
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Sources                            
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Packages                    
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Sources                      
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/multiverse Packages              
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages                       
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Packages                
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Sources                        
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/restricted Sources               
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages                     
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/main Sources                     
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Sources                      
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/multiverse Sources               
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages                   
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [ftp://ftp.mirrorservice.org](ftp://ftp.mirrorservice.org) gutsy-updates/universe Sources                 
  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages             
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Packages
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Sources
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve &#8216;archive.canonical.com&#8217;
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;archive.canonical.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz)  Could not resolve &#8216;archive.canonical.com&#8217;
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz)  Could not resolve &#8216;archive.canonical.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not resolve &#8216;security.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](ftp://ftp.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve &#8216;ftp.mirrorservice.org&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any other suggestions? Is this maybe a DNS issue?

---

### Post by Begemot74 on 2008-02-25
Update - I've added security.ubuntu.com to my etc/hosts file. This seems to have cured the problem, insofar as I can now download updates, but it does seem to suggest that there's a dns issue somewhere....
Thanks to all who've offered assistance.

---

### Post by seventhc on 2008-02-25
I think if it was a DNS issue you probably wouldn't get any web sites in your browser either.
Although it does seem to appear as one...(could not resolve)
but I still think then even your email and browsing wouldn't work.

---

### Post by sayakb on 2008-02-25
@OP
Check your Network Proxy settings for gnome for any invalid proxy server's IP address.

---

