---
title: "[SOLVED] Install VMware Server Problems"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by gavshouse on 2008-04-10
im having real problems installing VMware server 

ive tried this 
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

i have installed this before on the same machine but i did a fresh install

but i get this error

```

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_GB
Get: 1 http://archive.ubuntu.com gutsy Release.gpg [191B]                      
Hit http://archive.ubuntu.com gutsy/restricted Translation-en_GB               
Hit http://archive.ubuntu.com gutsy/universe Translation-en_GB                 
Hit http://archive.ubuntu.com gutsy/multiverse Translation-en_GB
Get: 2 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_GB
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.canonical.com gutsy Release 
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 2B in 0s (11B/s) 
Reading package lists... Done
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

The following packages have unmet dependencies.
  vmware-server: Depends: ia32-libs (>= 0.2) but it is not going to be installed
                 Depends: ia32-libs-gtk
                 Depends: libc6-i386 (>= 2.3.4-1) but it is not installable
E: Broken packages
```

So i tried Synaptic way

and i get this

```

vmware-server:
 Depends: ia32-libs but it is not going to be installed
 Depends: ia32-libs-gtk
 Depends: libc6-i386 (>=2.3.4-1) but it is not installable
```

Now ive installed this before any one got ideas

Also im having problems installing anything

VLC did this

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

This is a fresh install so whats going on

---

### Post by spiderbatdad on 2008-04-10
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zvacet on 2008-04-11
**System>admin>software source**s>check all under Ubuntu software and updates tab.Reload.Go to the** synaptic>edit tab>fix broken packages**.

---

### Post by gavshouse on 2008-04-12
i ended up re-installing its ok now, thanks anyway

---

