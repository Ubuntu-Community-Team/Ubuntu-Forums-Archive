---
title: "[SOLVED] Updates"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Lorac1949 on 2007-12-06
I noticed that there is a update to NDISWrapper on the Internet - 1.50.  I'm currently running 1.43.  I marked the NDISWrapper files for Update.  Then I ran Update Manager and it didn't see the 1.50 update.  Why is this?  Is this a *bug* in Gutsy's Update Manager?

---

### Post by taurus on 2007-12-06
What happens if you try to run the update/upgrade from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Martin Witte on 2007-12-06
the ubuntu repositories have version 1.43 learns a quick check of available packages in synaptic

---

### Post by Lorac1949 on 2007-12-06
> **taurus said:**
> What happens if you try to run the update/upgrade from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

Here's the output; no upgrades and I don't see ndiswrapper in the list:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_US               
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                                                   
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Fetched 4B in 0s (5B/s)  
Reading package lists... Done
carol@carol-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by taurus on 2007-12-06
Version in repos is not always the latest so unless you really want to use version 1.5, you need to install it yourself.

---

### Post by Lorac1949 on 2007-12-06
> **taurus said:**
> Version in repos is not always the latest so unless you really want to use version 1.5, you need to install it yourself.

Thanks, taurus.  I'm still a newbie, but I thought this was unusual.  I've been trying to make a wireless connection with my BCM43xx card.  The latest "fix" I've seen suggests using the 1.50 version of NDISWrapper.

---

