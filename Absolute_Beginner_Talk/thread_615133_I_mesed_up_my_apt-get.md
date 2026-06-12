---
title: "I mesed up my apt-get"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by elec999 on 2007-11-16
I did something to my apt-get, and now always get a error, no matter what I use with apt-get.
giant@GiantQ:~$ sudo apt-get install xmsensor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmsensor
giant@GiantQ:~$ sudo apt-get install xsensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnfnetlink0 libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lm-sensors
Suggested packages:
  sensord read-edid
The following NEW packages will be installed:
  lm-sensors xsensors
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 535kB of archives.
After unpacking 1761kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main lm-sensors 1:2.10.4-1ubuntu1 [509kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xsensors 0.50-1ubuntu1 [26.3kB]
Fetched 535kB in 2s (199kB/s) 
Selecting previously deselected package lm-sensors.
(Reading database ... 107730 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a2.10.4-1ubuntu1_i386.deb) ...
Selecting previously deselected package xsensors.
Unpacking xsensors (from .../xsensors_0.50-1ubuntu1_i386.deb) ...
Setting up linux-image-2.6.22-14-386 (2.6.22-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-386 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up lm-sensors (1:2.10.4-1ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing lm-sensors (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of xsensors:
 xsensors depends on lm-sensors; however:
  Package lm-sensors is not configured yet.
dpkg: error processing xsensors (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-386
 lm-sensors
 xsensors
E: Sub-process /usr/bin/dpkg returned an error code (1)
giant@GiantQ:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
The following packages were automatically installed and are no longer required:
  libnfnetlink0 libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-386 (2.6.22-14.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-386
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-386 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up lm-sensors (1:2.10.4-1ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing lm-sensors (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of xsensors:
 xsensors depends on lm-sensors; however:
  Package lm-sensors is not configured yet.
dpkg: error processing xsensors (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-386
 lm-sensors
 xsensors
E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks

---

### Post by taurus on 2007-11-16
Let's have a look at your /etc/apt/sources.list first.  Post

```
cat /etc/apt/sources.list
```

---

### Post by rexxxlo on 2007-11-16
not trying to thread jack but i get the same error 


here are my results to your code

> lolo@lolo-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
lolo@lolo-desktop:~$ 



---

### Post by taurus on 2007-11-16
> **rexxxlo said:**
> not trying to thread jack but i get the same error 

here are my results to your code

Can you post the output of this command from a terminal?

```
sudo apt-get update
```

---

### Post by rexxxlo on 2007-11-16
lolo@lolo-desktop:~$ sudo apt-get update
[sudo] password for lolo:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 5B in 0s (6B/s)  
Reading package lists... Done
lolo@lolo-desktop:~$

---

### Post by rexxxlo on 2007-11-16
hmm no error that time ?  wonder what hapened?

does that all look good ? what are you looking at ? is there something telling you that there is a problem?

---

### Post by taurus on 2007-11-16
Everything looks to be normal there.  Now, run the next command and see what happens.

```
sudo apt-get upgrade
```

---

### Post by rexxxlo on 2007-11-16
lolo@lolo-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 9290kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
lolo@lolo-desktop:~$ 

is this related to the bug i read about today?

---

### Post by taurus on 2007-11-16
Yes, it is.

[http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1)
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by rexxxlo on 2007-11-16
is this problem the reason i can not install any programs ? i get errors from the terminal or synaptic


thanks

---

### Post by taurus on 2007-11-16
> **rexxxlo said:**
> is this problem the reason i can not install any programs ? i get errors from the terminal or synaptic

thanks

Yes.  I would hold of on installing anything until tomorrow to see if the samba thing resolved by then.  But if you really need to install something, then you can remove those three files from your machine and see if you can install whatever you need to install.  Then, install those three samba files later.

---

### Post by elec999 on 2007-11-17
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
Thanks

---

### Post by taurus on 2007-11-17
Now see what happens if you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by elec999 on 2007-11-18
Tried both of those

Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9851kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109797 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
giant@GiantQ:~/vmware-player-distrib$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Get:4 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Packages
Hit [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) gutsy/main Sources
Fetched 4B in 1s (2B/s)
Reading package lists... Done
giant@GiantQ:~/vmware-player-distrib$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9851kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109797 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks

---

