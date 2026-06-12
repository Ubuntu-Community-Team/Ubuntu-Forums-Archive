---
title: "help! repositories dont work at all :("
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-09-12
Im using the repositories from ubuntu demon on the customization guide on this page but if I try to install anything from them they just dont find the package. :(

any help to get?

---

### Post by Jussi Kukkonen on 2006-09-12
We're not mind readers, you know? ;)

Please provide the following info
* link to the instructions you're using
* commands you used
* actual error messages you get

---

### Post by 3rr0r on 2006-09-12
did you enable multiverse and universe?

---

### Post by jcrnan on 2006-09-12
sorry. :/

list im using: [http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758) (with opened up skype/realplayer repositories)

Ive tried to install anything in the guide that ubuntu_demon provides there and also some of my own like sudo aptitude install kopete and similar.

example error:

silje@kitty:~$ sudo aptitude install mozilla-plugin-vlc
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "mozilla-plugin-vlc"No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
silje@kitty:~$

---

### Post by 3rr0r on 2006-09-12
So..............  multivers and universe, are they enabled or not?

---

### Post by Fully216 on 2006-09-12
Could you post your /etc/apt/sources.list.  Thanks!

---

### Post by jcrnan on 2006-09-12
uhm, I use the exact list I posted a link to.

but if you want me to post it here as well, sure:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
##currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
 deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by Fully216 on 2006-09-12
Both these repositories will work ... see links.

[http://morgoth.free.fr/ubports/#sourcelist](http://morgoth.free.fr/ubports/#sourcelist)
[http://gauvain.tuxfamily.org/repos/](http://gauvain.tuxfamily.org/repos/)

Don't forget you have to add/import the signing key to apt ... see link.

[http://morgoth.free.fr/ubports/#aptkey](http://morgoth.free.fr/ubports/#aptkey)

I would try those 'unofficial' to see if they work.

---

### Post by jcrnan on 2006-09-12
not working at all. still same error, etc.

---

### Post by Jussi Kukkonen on 2006-09-12
mozilla-plugin-vlc is in universe and that is enabled in the sources.list you provided. I can only think that you might have forgotten to 
```
sudo aptitude update
```
before you tried to install stuff...

---

### Post by Fully216 on 2006-09-12
This is strange because I just installed it by adding those repos, just to make sure it could be done.  Hmmm ... to be honest I am not sure what the issue is then, especially if you added the signing key.  ](*,)

---

### Post by jcrnan on 2006-09-13
Uhm, it somehow suddenly started working again. But Im having some problems with broken packages and umet dependencies.

Im getting errors like theese:

 The following packages have unmet dependencies:
  vlc: Depends: libdc1394-13 which is a virtual package.
       Depends: libdvdnav4 (>= 0.1.9) which is a virtual package.
       Depends: libdvdread3 which is a virtual package.
       Depends: libgsm1 (>= 1.0.10) which is a virtual package.
       Depends: libid3tag0 (>= 0.15.1b) which is a virtual package.
       Depends: libmad0 (>= 0.15.1b) which is a virtual package.
       Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.
       Depends: libmpcdec3 which is a virtual package.
Resolving dependencies...

and

The following packages are BROKEN:
  vlc

and

The following packages have unmet dependencies:
  libxine-main1: Depends: libmodplug0c2 (>= 1:0.7-4.1) which is a virtual package.

and

No candidate version found for mplayer
The following packages are BROKEN:
  libxine-main1 vlc

and

The following packages have unmet dependencies.
  totem-gstreamer-firefox-plugin: Depends: totem-gstreamer (= 1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed
E: Broken packages

---

### Post by jcrnan on 2006-09-13
meh, doesnt look like other things are working afterall.. just a few packages that got installed.. false hope :/

---

### Post by Jussi Kukkonen on 2006-09-13
> **jcrnan said:**
> meh, doesnt look like other things are working afterall.. just a few packages that got installed.. false hope :/
Please paste the commands you used and the response you got. Otherwise helping is difficult.

If your packages are still somehow broken, try this:
* run *apt-get update* and make sure there are no errors
* run *apt-get install -f*
That should make sure you have good package lists, and that your installed packages are fine. If everything seems fine, try installing the packages you wanted. If not, paste any errors here.

---

### Post by jcrnan on 2006-09-13
okey, so errors on apt-get update:

silje@kitty:~$ sudo apt-get update
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://download.skype.com](http://download.skype.com) stable Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) dapper Release.gpg
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [821kB]
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [5292B]
99% [8 Packages gzip 0] [9 Packages 4952/5292B 93%] [Connecting to gandalfn.clu
gzip: stdin: not in gzip format
Errhttp://archive.ubuntu.com dapper/main Packages
  Sub-process gzip returned an error code (1)
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [3486B]
Get: 13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get: 14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
99% [14 Packages gzip 0] [Waiting for headers] [Connecting to gandalfn.club.fr
gzip: stdin: not in gzip format
Errhttp://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get: 15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [97.9kB]
99% [15 Packages gzip 0] [Connecting to gandalfn.club.fr (194.158.120.142)]
gzip: stdin: not in gzip format
Errhttp://archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) dapper/. Packages
Hit [http://gandalfn.club.fr](http://gandalfn.club.fr) dapper/. Packages
Fetched 8856B in 17s (493B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


errors on apt-get install -f:

silje@kitty:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.



edit: I also get this error when I tried installing some of the packages in synaptics: 

totem-gstreamer-firefox-plugin:
  Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed

do I have a wrong ubuntu version or something? :S *confused*

---

### Post by Jussi Kukkonen on 2006-09-13
Looks like your current packages are fine (*install -f* didn't complain anything), but there's something wrong with updating the installable package lists: (Some index files failed to be opened as .gz-files). This is probably why installing new stuff fails too...

I just did a search, and found out that this could be a firewall/proxy issue -- are you behind one? Some filter proxies just prevent (some) .gz files from being downloaded (and replace them with a html file with a error message!). try this:
```
wget -nv http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz
file Packages.gz

```
the last command should tell you if you're receiving a gzip compressed file or something else...

---

