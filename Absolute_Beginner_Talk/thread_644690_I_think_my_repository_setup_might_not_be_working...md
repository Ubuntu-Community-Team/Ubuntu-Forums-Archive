---
title: "I think my repository setup might not be working..."
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2007-12-19
I just did a complete reinstall of Gutsy Gibbon.

I'm trying to get compiz fusion to work.

I am following the steps here:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

When I click the link for:
apt:compizconfig-settings-manager

Ubuntu pops up a window that says "Can not find 'compizconfig-settings-manager' ".

How can I check to see if my repository settings are OK?

---

### Post by forestpixie on 2007-12-19
try doing it in a terminal and post the output of it and your sources.list

```
sudo apt-get install compizconfig-settings-manager
```
```
cat /etc/apt/sources.list
```

---

### Post by discoade on 2007-12-19
you need to install compizconfig-settings-manager try typing it into synaptic packet manager search and install it

beat me to it!

---

### Post by joesmith1234 on 2007-12-19
> **forestpixie said:**
> try doing it in a terminal and post the output of it and your sources.list

```
sudo apt-get install compizconfig-settings-manager
```
```
cat /etc/apt/sources.list
```

thuskins@thuskins-desktop:~$ man ccsm
No manual entry for ccsm
thuskins@thuskins-desktop:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
You will have to enable component called 'universe'
bash: ccsm: command not found
thuskins@thuskins-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for thuskins:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
thuskins@thuskins-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
thuskins@thuskins-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
thuskins@thuskins-desktop:~$

---

### Post by joesmith1234 on 2007-12-19
So from the above info... I'm not sure of the best way to correct the problem...

---

### Post by overdrank on 2007-12-19
> **joesmith1234 said:**
> thuskins@thuskins-desktop:~$ man ccsm
No manual entry for ccsm
thuskins@thuskins-desktop:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
You will have to enable component called 'universe'
bash: ccsm: command not found
thuskins@thuskins-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for thuskins:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
thuskins@thuskins-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
thuskins@thuskins-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
[COLOR="Red"]#[/COLOR]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
thuskins@thuskins-desktop:~$

Hi and you need to uncomment your repos  # the comment like I have highlighted on the last line. And you can also remove # Line commented out by installer because it failed to verify:
This command will allow you to edit your sources list ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by joesmith1234 on 2007-12-19
> **overdrank said:**
> Hi and you need to uncomment your repos  # the comment like I have highlighted on the last line. And you can also remove # Line commented out by installer because it failed to verify:
This command will allow you to edit your sources list ```
gksudo gedit /etc/apt/sources.list
```

Sorry, I don't understand.

So I take the # away from the sources.list file?

Why did they fail to verify?

---

### Post by forestpixie on 2007-12-19
if the internet wasn't working when you installed or upgraded they get marked like that

as far as the #'s go - a line gets ignored if it has a # - so for each line you want apt to use remove the #, I would, unless you know you need the sources, leave the # for the deb-src lines, and obviously leeve the # in front of 'writing'

> Feliz Navidad - Overdrank :)

---

### Post by joesmith1234 on 2007-12-20
Ok, I modified the sources file, but it still won't find the compiz package...

```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fi.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

And then I logged out, logged back in, and then...

```

thuskins@thuskins-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
thuskins@thuskins-desktop:~$ 

```

---

### Post by forestpixie on 2007-12-20
did you do a apt-get update and try commenting out the cdrom on the first line

---

### Post by joesmith1234 on 2007-12-20
> **forestpixie said:**
> did you do a apt-get update and try commenting out the cdrom on the first line

no, how do I do an apt-get update?

---

### Post by overdrank on 2007-12-20
> **joesmith1234 said:**
> no, how do I do an apt-get update?

Hi and in the terminal use the command ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by joesmith1234 on 2007-12-21
> **overdrank said:**
> Hi and in the terminal use the command ```
sudo apt-get update
sudo apt-get upgrade
```

Ok, now I really don't understand...  I can't connect to these fi.archive.ubuntu locations or anything through the update, but I can type them directly into firefox and they work fine....
any ideas anyone?

```

thuskins@thuskins-desktop:~$ sudo apt-get update
[sudo] password for thuskins:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://fi.archive.ubuntu.com gutsy Release.gpg                             
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://archive.canonical.com gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://fi.archive.ubuntu.com gutsy/main Translation-en_US                  
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://archive.canonical.com gutsy/partner Translation-en_US               
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err http://security.ubuntu.com gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Err http://fi.archive.ubuntu.com gutsy/restricted Translation-en_US            
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy/universe Translation-en_US              
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://security.ubuntu.com gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Err http://fi.archive.ubuntu.com gutsy/multiverse Translation-en_US            
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-updates Release.gpg                     
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Err http://fi.archive.ubuntu.com gutsy-updates/main Translation-en_US          
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US       
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Err http://fi.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Err http://fi.archive.ubuntu.com gutsy-backports Release.gpg                   
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-backports/main Translation-en_US
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-backports/universe Translation-en_US
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Err http://fi.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://fi.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to fi.archive.ubuntu.com:80 (193.166.3.5), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out [IP: 91.189.88.37 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
thuskins@thuskins-desktop:~$ 

```

---

### Post by joesmith1234 on 2007-12-21
> **joesmith1234 said:**
> Ok, now I really don't understand...  I can't connect to these fi.archive.ubuntu locations or anything through the update, but I can type them directly into firefox and they work fine....
any ideas anyone?


ok, forget this... I had to add an http proxy to my etc/environment file.
i could connect with firefox because it had the autoproxy configuration set up.

---

### Post by forestpixie on 2007-12-21
I don't know much about using proxies (proxys?) at all - but I know you can set up synaptic to do so - settings, network

---

