---
title: "Is it possible to upgrade from gOS 2 to Xubuntu 8.0.4?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by newbjeff on 2008-04-10
I am currently running gOS 2.0.1 beta and am thinking to switch to Xubuntu when the new version is released.  Does anyone know if I will be able to do that as an upgrade or will I have to format my drive to add the new OS?  :confused:

---

### Post by meborc on 2008-04-10
> **newbjeff said:**
> I am currently running gOS 2.0.1 beta and am thinking to switch to Xubuntu when the new version is released.  Does anyone know if I will be able to do that as an upgrade or will I have to format my drive to add the new OS?  :confused:

you can try :) if it fails, you will need to format anyway
[U]
i do not believe this will work[/U], so**[COLOR="DarkRed"] back up[/COLOR]** everything before continuing!!!

if you really want to go through with it do:

```
sudo gedit /etc/apt/sources.list
```

copy this over whatever you have in there:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

deb [http://debian.ettin.org/allacrost](http://debian.ettin.org/allacrost) unstable main

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://ppa.launchpad.net/envyng-hardy/ubuntu](http://ppa.launchpad.net/envyng-hardy/ubuntu) hardy main


save and close

then
```

sudo apt-get update
sudo apt-get dist-upgrade -f -o DPkg::options::="--force-overwrite"
sudo apt-get install xubuntu-desktop
```

---

### Post by newbjeff on 2008-04-10
Thanks for your helpful response.  As you said, if upgrade fails I can always start fresh.  ;)

Regards,

Jeff

---

### Post by Flying caveman on 2008-04-10
I'm pretty sure its possible, I went from a gOS install when it first came out to a regular Ubuntu install (can't remember what the version was at the time) I just added the regular Ubuntu repositories and installed the ubuntu desktop. ```
apt-get install ubuntu-desktop
```  Some of the green gOS theme was persistent though,  I think I had to change the boot splash, and some of the desktop theme attributes to get rid of some of the Greenness.

---

