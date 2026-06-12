---
title: "Installing Wine."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by bernard12345 on 2008-02-01
```
andrew@andrew-desktop:~$ wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
OK
andrew@andrew-desktop:~$ sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.lis
--21:05:05--  http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list
           => `/etc/apt/sources.list.d/winehq.lis'
Resolving wine.budgetdedicated.com... 81.171.111.184, 88.159.206.7, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

21:05:05 (14.54 MB/s) - `/etc/apt/sources.list.d/winehq.lis' saved [181/181]

andrew@andrew-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://wine.budgetdedicated.com gutsy Release.gpg [191B]  
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US
Hit http://wine.budgetdedicated.com gutsy Release
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Fetched 191B in 1s (166B/s)
Reading package lists... Done
andrew@andrew-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
andrew@andrew-desktop:~$ 

```

This is what i've done as far as installing it however - it doesn't seem to have installed.  Any help would be great!

Thanks.

---

### Post by taurus on 2008-02-01
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for all the lines except the last one, Source code, and Cdrom in the window below.  Close it and press Refresh.  Now, see if you can find wine from the Search field and install it from there.  Otherwise, shutdown synaptic and install it with apt-get from a terminal again.

---

### Post by JoshuaRL on 2008-02-01
Could you post the output of:
```

gksu gedit /etc/apt/sources.list

```

Just wondering if you have all the repos uncommented.

Also, I would always suggest getting the newest version of Wine.  The one in the repos is older, and may not support as much.

Try doing these in order.  Each line should be separate commands.
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine

```

---

### Post by bernard12345 on 2008-02-01
> **JoshuaRL said:**
> Could you post the output of:
```

gksu gedit /etc/apt/sources.list

```

Just wondering if you have all the repos uncommented.
All of them are commented - which would you suggest i uncomment?

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by spiderbatdad on 2008-02-01
all but backports

---

### Post by bernard12345 on 2008-02-01
> **taurus said:**
> Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for all the lines except the last one, Source code, and Cdrom in the window below.  Close it and press Refresh.  Now, see if you can find wine from the Search field and install it from there.  Otherwise, shutdown synaptic and install it with apt-get from a terminal again.
Worked like a charm thank you for the help!

---

### Post by JoshuaRL on 2008-02-01
You can either follow Taurus' excellent advice, or manually take out every # at the beginning of any line that starts with something like:
> 
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

and make it look like:
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

Then save it with the same file name and overwrite the existing file.  Then follow those directions to get wine.

---

