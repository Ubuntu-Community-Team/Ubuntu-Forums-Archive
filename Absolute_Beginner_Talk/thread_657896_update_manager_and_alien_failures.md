---
title: "update manager and alien failures"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by cortical on 2008-01-04
2 possibly related problems

1. have installed Ubuntu 7.10, and finally got a modem connection working.
When connected, launched Update manager, which fell over reporting:

Could not initialize the package information, , an unresolvable problem occured while initializing the package information...
E: read error - read/5 input/output error
E: the package lists or status files could not be parsed or opened

restarted and repeated, got the same result.


2. need to install printer drivers for a Canon 1250
as the printer is recognised and a generic pdriver assigned, but does not print.
So after finding some methods to deal with this, downloaded rpm packages, which I need alien for to convert to deb... as I understand things. (have been through several dpkg -i ...)


have tried to install, and remove alien.... but all attempts stymied


cb@ublx:~$ cd Desktop
cb@ublx:~/Desktop$ sudo dpkg -i alien_8.64_all.deb
Bus error (core dumped)
cb@ublx:~/Desktop$ sudo apt-get remove --purge alien_8.64_all.deb
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~/Desktop$ sudo apt-get remove --purge alien_8.64_all.deb
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~/Desktop$ sudo apt-get install libpng3 libtiff4 cupsys alien
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~/Desktop$ 


any suggestions as to what approach to take?

---

### Post by RomeReactor on 2008-01-04
Hi. You may have a problem with your sources file; open a terminal and please post the output of this:
```
cat /etc/apt/sources.list
```
Does internet access work correctly?

---

### Post by cortical on 2008-01-06
thanksRR:

cb@ublx:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
cb@ublx:~$

---

### Post by cortical on 2008-01-06
internet access works ok via wvdial/Gnomeppp: firefox, and mail

---

### Post by forestpixie on 2008-01-06
have a look at this thread, you need to edit your sources.list. Half way down it shows you how to edit it

[http://ubuntuforums.org/showthread.php?t=659314](http://ubuntuforums.org/showthread.php?t=659314)

---

### Post by adam.tropics on 2008-01-06
@forestpixie: Nice gentle guide you posted there, by the way, I seem to be noticing this crop up alot lately (sources with no sources!!) any idea why?

---

### Post by forestpixie on 2008-01-06
believe it's something to do with the way the installer works - if there's no net connection or it can't phone home to verify the repos it appears to stop them all and just leave the cdrom as the source

I got fed up with typing the same thing for different people - so did it once :)

If you by any chance know the xubuntu version of gksudo gedit - I'd appreciate that

did think about getting them to sticky it - I'm sure evryone is as fedup with it as I am

---

### Post by adam.tropics on 2008-01-06
> **forestpixie said:**
> believe it's something to do with the way the installer works - if there's no net connection or it can't phone home to verify the repos it appears to stop them all and just leave the cdrom as the source

I got fed up with typing the same thing for different people - so did it once :)

If you by any chance know the xubuntu version of gksudo gedit - I'd appreciate that

did think about getting them to sticky it - I'm sure evryone is as fedup with it as I am

I think mousepad is the text editor in xubuntu, and I guess gksudo is still correct. You should get them to sticky it...that or post it again to the 'tips and tutorials' forum.

---

### Post by forestpixie on 2008-01-06
thanks for that - I'll change it to show mousepad - checked and you're correct

maybe I'll see if they'll sticky it here - I didn't even know there was a tips and tutorials forum - so I guess someone who's just turned up with a new install isn't likely to either :)

thanks for the vote of confidence

---

### Post by cortical on 2008-01-06
> **forestpixie said:**
> have a look at this thread, you need to edit your sources.list. Half way down it shows you how to edit it

[http://ubuntuforums.org/showthread.php?t=659314](http://ubuntuforums.org/showthread.php?t=659314)


followed instructions on this, and it fell over:

cb@ublx:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Translation-en_AU
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_AU
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_AU
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release [65.9kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_AU
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release [58.5kB]              
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages [1075kB]                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [8655B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [29.3kB]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [4609B]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2903B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [20B]      
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Packages [7664B]          
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Sources [306kB]                 
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Sources [2120B]           
Get:17 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages [4065kB]           
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Sources [1226kB]                                              
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Packages [158kB]                                            
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Sources [56.8kB]                                            
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages [112kB]                                          
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]                                    
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Sources [28.4kB]                                          
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]                                      
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Packages [44.1kB]
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/universe Sources [7787B]                                       
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Packages [9215B]                                    
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Sources [1702B]                                     
Fetched 7327kB in 1h18m7s (1563B/s)
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~$ 

It is something of a problem that once initiated, one has no idea how many packages the process is going to (presumably) download. On a modem connection on this one, time was also a concern

Is theer a means of having it evaluate how many packages it pans to download, before tahht is executed?


In order to reduce the complexity/time, I redited the sources list for just main restricted, and ran it again. This also fell over.:


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

>>>

cb@ublx:~$ sudo gedit /etc/apt/sources.list
[sudo] password for cb:
cb@ublx:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release [58.5kB]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages [112kB]                           
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]                     
Fetched 175kB in 2m55s (995B/s)                                                                  
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~$

---

