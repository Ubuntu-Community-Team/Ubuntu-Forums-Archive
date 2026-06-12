---
title: "Error using sudo apt-get install [anything]"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]Hi all, I installed Ubuntu last night, and today I decided to try and install Opera, I followed the instructions I found on a wiki (can't remember the link) but everytime I tried I got an error:

[QUOTE=Terminal]E: Type ‘“deb’ is not known on line 75 in source list /etc/apt/sources.list
E: The list of sources could not be read.[/QUOTE]

I'm not sure whats happened, I'm guessing it an error on my behalf as I'm new to Ubuntu, so if anyone can see what I've done wrong I would be extreamely grateful.

Thanks.
-Aura[/COLOR]

---

### Post by ThrobbingBrain66 on 2008-01-13
There is an error in your sources.list file.  Enter the following command in the terminal and then post the output here:

```
cat /etc/apt/sources.list
```

---

### Post by overdrank on 2008-01-13
> **Auraomega said:**
> [COLOR="Purple"]Hi all, I installed Ubuntu last night, and today I decided to try and install Opera, I followed the instructions I found on a wiki (can't remember the link) but everytime I tried I got an error:



I'm not sure whats happened, I'm guessing it an error on my behalf as I'm new to Ubuntu, so if anyone can see what I've done wrong I would be extreamely grateful.

Thanks.
-Aura[/COLOR]

HI and you can use this command to edit that line in you sources list on line 75
```
gksudo gedit /etc/apt/sources.list
```
Edit to slow lol

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]Thanks for the swift reply, the output is:

[QUOTE=Terminal]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy restricted main universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
[/QUOTE]

I just commented out the 75th line, but got an error telling me the software index was broken.

Thanks again.
-Aura[/COLOR]

---

### Post by ThrobbingBrain66 on 2008-01-13
First, on the very last line of that file, you have to remove the quotation mark (") from the beginning of the line.  Oh, and you're using Gutsy, so you shouldn't be using the Automatix repo for Feisty.

Second, all your repos are commented out.  Have you received any updates since your last upgrade/install?  Basically, every line that starts with 'deb' or 'deb-src' needs to have the pound sign (#) removed from the beginning.

Open the file in Gedit, and make your changes:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by edm1 on 2008-01-13
Also on your last line it should be gusty instead of feisty. I would use synaptic to enable all my repositories, it will be easier. In synaptic go setting>repositories then make sure all the boxes are ticked except 'source code'.

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]My computer is now refusing to connect to the net, point blank, so I can't do much at all...

I read somewhere that you can install on a FAT32 format, I tried but couldn't get it to install, I think I may re-install Ubuntu to try and fix the problem (I haven't actually done anything on there yet that I can't back up), I was just wondering if someone could tell me what I need to do to get it FAT32, I tried making the root / but it wouldn't allow me to continue.

Thanks again.
-Aura[/COLOR]

---

### Post by edm1 on 2008-01-13
Why would you want FAT32? It has nothing to do with the above problem. Have you tried doing what i recommended above? I forgot to add that after enabling the repositories you must press 'reload' in synaptic.

---

### Post by flamelab on 2008-01-13
Comment (put #) before the Automatix repo 

and 

uncomment all the line that start with "deb" in the beginning

then on terminal enter

```
sudo -s -H
```

```
apt-get update 
```

```
apt-get upgrade
```

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]I tried, and it fixed the problems, but as I said, it now refuses to connect to the net at all, so I can't install anything, it won't even recognise my wlan adaptor anymore. The reason I said FAT32 is so I can access it easily with an install of XP, and because I think I might do a fresh install of Ubuntu to fix the problems.

-Aura[/COLOR]

---

### Post by taurus on 2008-01-13
Installing Ubuntu on a  fat32 partition is a real bad idea.  If you want to access Ubuntu from XP, you can use fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Otherwise, create another partition as fat32 and share it between Ubuntu and XP.

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]Ok thanks, any quick advice that may get me up and running with the net, or would it be faster to do a fresh install?

-Aura[/COLOR]

---

### Post by edm1 on 2008-01-13
Well what is not working about the internet? Wired/wireless? Was it working before? Any error messages?

---

### Post by jrev on 2008-01-13
***_You cannot install Ubuntu on a vfat system _***

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]I'm using wireless, it was working fine before I got all the error messages when trying to install Opera.

No error messages, but on the network config (or whatever its called, can't remember exactly) there used to be an option for wlan0 but thats dissapeared, and the "network" bit won't save my password, I enter it and every time I check it again its dissapeared, or been replaced with a very long password.

-Aura[/COLOR]

---

### Post by Auraomega on 2008-01-13
[COLOR="Purple"]Just decided to boot up again to have another shot at getting a connection, and I'm getting a black screen with error messages on, they are all the same - usb 4-1 device descriptor read/64, error -110 or usb 4-1 device descriptor read/8, error -110, they alternate between the 64 and 8 every 4 errors. I think I'm going to re-install now...

-Aura[/COLOR]

---

