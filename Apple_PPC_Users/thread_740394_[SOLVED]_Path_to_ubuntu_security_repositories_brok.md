---
title: "[SOLVED] Path to ubuntu security repositories broken..."
date: 2008-03-30
forum: Apple PPC Users
---

### Post by somethingkindawierd on 2008-03-30
I am getting an error when running the Update Manager and I am not sure if the error is on my computer or on the server hosting the files.  

I recieve this error:
"Could not download all repository indexes"

These are the urls that are not available:
```
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/source/Sources.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/source/Sources.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/source/Sources.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/source/Sources.gz
```

Following the above urls back a few folders I find that these do exist:
```
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/binary-powerpc/Packages.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/binary-powerpc/Packages.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/binary-powerpc/Packages.gz
http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/binary-powerpc/Packages.gz
```

Are these urls the ones I need?  And if so how can I tell Ubuntu to look for these new urls?

---

### Post by stream303 on 2008-03-31
Same problem here on my Hardy - Beta install.  I'm not sure that they are broken - possibly just not activated since we're in beta / rc mode right now...  Probably all security updates are just coming through normal repositories for the time being...

---

### Post by maace on 2008-04-06
I'm having the same problem.  
Just put xubuntu 7.10 for powerpc onto an NewWorld iMac (Model M5521)

---

### Post by stream303 on 2008-04-07
If you are using the gui Software-Sources setup, I am no longer having any problems, but note that I have NO repositories selected in the first Ubuntu tab, and ONLY have the Ubuntu repositories checked off under "third party software", which I guess is normal for beta/port release?

Seems to override the /etc/apt/sources.list, so perhaps check your gui source preferences...

---

### Post by somethingkindawierd on 2008-04-07
I submitted this [as a bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/213112") a while back and Colin was kind enough to point out that the bug has been fixed, but for those of us upgrading prior to the fix we will have to fiddle to get it working.

I appear to have fixed it by doing the following:

1) Edit the source.list file
```
sudo gedit /etc/apt/sources.list
```
2) In gedit do a find-and-replace.  Replace all occurrences of 
```
http://ports.ubuntu.com/ubuntu-ports/
```
with
```
http://archive.ubuntu.com/ubuntu/
```
3) Save the sources.list file.  Opening the Software Sources app should show a very different (and in my case much shorter) list of sources in the Third Party Sources tab.  This now matches the installation I have on my Intel iMac.  I had to check the two sources here to make them active.
4) Opening Update Manager and checking for new updates should return a fresh list of updates. :)

---

### Post by stream303 on 2008-04-07
You rock!  Thank you so much, my repositories are very happy now!

---

### Post by mikmark on 2008-04-11
Probably all security updates are just coming through normal repositories for the time being...

---

### Post by stream303 on 2008-04-21
This time it is Xubuntu Hardy-RC from the 20 April daily image!

Seems that the deb-src repos are listed correctly, but all the normal deb sources still point to ubuntu-ports.  Had to apply this fix manually to my /etc/apt/sources.list.

With it only half-fixed, that would have freaked me out if it wasn't for you guys with these tips!  Thanks again.

Egads!  Seems I caught this thing in the middle of a transition!  Be SURE to see Colin's notes
[http://www.xubuntu.org/news/hardy/ports](http://www.xubuntu.org/news/hardy/ports)
Looks like I'll be changing my sources back to ports.ubuntu.com/ubuntu-ports very soon.

---

### Post by slacka-vt on 2008-04-24
I've been mucking around with this for 2 days now.
Still not sure what the right repos are since they've obviously changed.
Maybe they are just temporarily not working ?

```
autumn@ubuntu-ppc64:/etc/apt$ sudo aptitude update
Hit http://ports.ubuntu.com hardy Release.gpg
Ign http://ports.ubuntu.com hardy/main Translation-en_US
Ign http://ports.ubuntu.com hardy/restricted Translation-en_US
Ign http://ports.ubuntu.com hardy/universe Translation-en_US
Ign http://ports.ubuntu.com hardy/multiverse Translation-en_US
Hit http://ports.ubuntu.com hardy-updates Release.gpg
Ign http://ports.ubuntu.com hardy-updates/main Translation-en_US
Ign http://ports.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://ports.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://ports.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://ports.ubuntu.com hardy-security Release.gpg
Ign http://ports.ubuntu.com hardy-security/main Translation-en_US
Ign http://ports.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://ports.ubuntu.com hardy-security/universe Translation-en_US
Ign http://ports.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://ports.ubuntu.com hardy Release
Hit http://ports.ubuntu.com hardy-updates Release
Hit http://ports.ubuntu.com hardy-security Release
Hit http://ports.ubuntu.com hardy/main Packages
Hit http://ports.ubuntu.com hardy/restricted Packages
Ign http://ports.ubuntu.com hardy/main Sources
Ign http://ports.ubuntu.com hardy/restricted Sources
Hit http://ports.ubuntu.com hardy/universe Packages
Ign http://ports.ubuntu.com hardy/universe Sources
Hit http://ports.ubuntu.com hardy/multiverse Packages
Ign http://ports.ubuntu.com hardy/multiverse Sources
Hit http://ports.ubuntu.com hardy-updates/main Packages
Hit http://ports.ubuntu.com hardy-updates/restricted Packages
Ign http://ports.ubuntu.com hardy-updates/main Sources
Ign http://ports.ubuntu.com hardy-updates/restricted Sources
Hit http://ports.ubuntu.com hardy-updates/universe Packages
Ign http://ports.ubuntu.com hardy-updates/universe Sources
Hit http://ports.ubuntu.com hardy-updates/multiverse Packages
Ign http://ports.ubuntu.com hardy-updates/multiverse Sources
Hit http://ports.ubuntu.com hardy-security/main Packages
Hit http://ports.ubuntu.com hardy-security/restricted Packages
Ign http://ports.ubuntu.com hardy-security/main Sources
Ign http://ports.ubuntu.com hardy-security/restricted Sources
Hit http://ports.ubuntu.com hardy-security/universe Packages
Ign http://ports.ubuntu.com hardy-security/universe Sources
Hit http://ports.ubuntu.com hardy-security/multiverse Packages
Ign http://ports.ubuntu.com hardy-security/multiverse Sources
Err http://ports.ubuntu.com hardy/main Sources
  404 Not Found
Err http://ports.ubuntu.com hardy/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com hardy/universe Sources
  404 Not Found
Err http://ports.ubuntu.com hardy/multiverse Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-updates/main Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-updates/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-updates/universe Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-updates/multiverse Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-security/main Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-security/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-security/universe Sources
  404 Not Found
Err http://ports.ubuntu.com hardy-security/multiverse Sources
  404 Not Found
Reading package lists... Done
autumn@ubuntu-ppc64:/etc/apt$ 
```

here's my sources list:

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha powerpc (20080314)]/ hardy main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy universe
deb http://ports.ubuntu.com/ubuntu-ports/  hardy-updates universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://ports.ubuntu.com/ubuntu-ports hardy partner
# deb-src http://ports.ubuntu.com/ubuntu-ports hardy partner

deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
```

Thanks!

Edit: It just occurred to me that with the official release, the mirrors are probably being "hammered" causing me to "time-out" and receive a 404 error.

What you think ?

~s

---

### Post by BladeMelbourne on 2008-04-26
The mirrors and servers are probably under a higher load than usual, but that does not explain an HTTP 404 error (which means that the requested file was not found on the server).

Updates have not been working for days now. It looks like only i386 and amd64 packages are available...

[http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/]("http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/")

[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/")

Does anyone know where a working ppc repository is?

---

### Post by somethingkindawierd on 2008-04-26
Checkout the release notes here: [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

It says the urls have chaged.

> ...accordingly these architectures have been moved to     [ports.ubuntu.com]("http://ports.ubuntu.com/"). Users of these architectures should take care to     update /etc/apt/sources.list. Old sources.list entries looked like this (perhaps using <country>.[archive.ubuntu.com]("http://archive.ubuntu.com/") rather than [archive.ubuntu.com]("http://archive.ubuntu.com/")):     
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted[FONT=monospace]
[/FONT]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted     

while new entries should look like this:     [FONT=monospace]
[/FONT]deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy main restricted[FONT=monospace]
[/FONT]deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy-security main restrictedI made those changes and it kinda helped - I now get a few updates.  However, I still get 404 errors on any urls pointing at sources.

> Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/main/source/Sources.gz](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/main/source/Sources.gz)  404 Not Found
...
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by BladeMelbourne on 2008-04-26
Well I made the change to: 

```
deb http://ports.ubuntu.com/ubuntu-ports hardy restricted main multiverse universe
deb http://ports.ubuntu.com/ubuntu-ports hardy-updates restricted main multiverse universe
deb http://ports.ubuntu.com/ubuntu-ports hardy-security restricted main multiverse universe
deb http://ports.ubuntu.com/ubuntu-ports hardy-proposed restricted main multiverse universe
#deb http://ports.ubuntu.com/ubuntu-ports hardy-backports restricted main multiverse universe
deb http://archive.canonical.com/ubuntu hardy partner

# Multimedia
##deb http://www.debian-multimedia.org sid main
deb http://www.debian-multimedia.org unstable main
deb http://packages.medibuntu.org/ hardy free non-free
```

Now I get no 404s. There was only one new update (which didn't have a Ubuntu icon next to it). When I compile fuse/ntfs/xserver-xorg-video-ati I download the source from the project website. Not having sources makes apt-get update work a lot faster anyway.

---

### Post by urschrei on 2008-06-27
Is there a full list of working PPC repos available somewhere? Including things like backports?

---

### Post by stream303 on 2008-06-27
ports.ubuntu.com/ubuntu-ports is the only place to get it now that the mirrors don't carry the ppc port repos to save on space and bandwidth.

Once the list is edited, you just uncomment the backport repository, or if using the gui, look into the "third party" tab, where our software sources now reside, even though you could say we aren't really third-party. :)

---

### Post by deep32 on 2008-06-28
May be it is possible that all security updates are just coming through normal repositiors for the time being.

---

### Post by stream303 on 2008-06-29
I think so, but maybe in the form of redirects to the new repos.  I know that when I was using late Hardy beta's, you had to edit the file.

That's a good question, especially for Dapper users.  Did they have to edit the sources.list file too to point to the new repos, especially if they paid for commercial support?  If not, maybe page redirects are helping out, and may be gone once Dapper goes EOL.

---

