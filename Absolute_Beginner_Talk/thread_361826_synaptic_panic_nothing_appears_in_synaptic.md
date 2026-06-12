---
title: "synaptic panic: nothing appears in synaptic"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by wantime on 2007-02-14
Hi,

I've been trying to install a brother printer and seem to have bungled something up very much.

Even after a restart I get this message box when I open Synaptic:

```
Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems.
 If available an older version of the failed index will be used. Otherwise the repository will be ignored. 
Check your network connection and the correct writing of the repository address in the preferences.

```

Is there an easy way to fix this??

Thanks

---

### Post by batholith on 2007-02-14
please post the contents of /etc/apt/sources.list

---

### Post by wantime on 2007-02-14
OK, here is the sources.list ..

```
 cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

```

Thanks

---

### Post by batholith on 2007-02-14
OK here's your sources.list...I highlighted a couple  [SIZE="5"]#[/SIZE]'s in red which i think you should remove (thereby activating the repository)...a easy way to do this is through the command line (terminal) with the following commands:

$sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

This make a backup copy in case things go really wrong...

then:

$sudo gedit /etc/apt/sources.list

This opens gedit in which you can edit and save your file...

```
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
[COLOR="Red"]#[/COLOR] deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
# deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
[COLOR="Red"]#[/COLOR] deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main
## Listen
# deb http://theli.free.fr/packages/ edgy listen

```

I'd make and save the changes and try synaptic again...if that doesn't work, try going to the terminal and typing the following:

$sudo apt-get update

This is basically the command line version of synaptic.   If that doesn't work, post the errors...other than that, I'm at a loss...hopefully someone else can point you in a better direction

---

### Post by wantime on 2007-02-14
So I have now changed the sources.list and still Synaptic gets an error message on startup.  When I try reloading it seems to be timing out on the last two packages.

Using:

```
$sudo apt-get update

I get the timeouts on the freecontrib.org repositories with the messages as follows:

Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg                           
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 6B in 6m0s (0B/s)                                 
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Other than that I have posted a bug report .. Thanks for the help.

---

### Post by wantime on 2007-02-14
OK, so I think that I have fixed the problem.  At least my Synaptic is working again.

I manually tried removing the mfc440cncupswrapper package using dpkg to no avail.

One of the error messages was:

```
sudo dpkg -r mfc440cncupswrapper
(Reading database ... 108577 files and directories currently installed.)
Removing mfc440cncupswrapper ...
/var/lib/dpkg/info/mfc440cncupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc440cn/cupswrapper/cupswrappermfc440cn: not found
dpkg: error processing mfc440cncupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 mfc440cncupswrapper

```

So, I went into the /usr/local/  and recursively deleted the Brother directory.  Now I am back to square one.

---

### Post by batholith on 2007-02-15
Sounds to me like the repositories under the "freecontrib" don't appear to be working properly..perhaps not setting up dependencies correctly, or just not transferring...  I can't help with that..but at least you've got synaptic back up and running properly.  

If I were you, I'd try to find some other outlets for Brother drivers...if they're out there??  Good Luck!

---

### Post by wantime on 2007-02-15
Yeah, they weren't working, I took them off the list and things ran smoother ... still tweeking a lot as I have just reinstalled and upgraded from Dapper.  And will continue with the printer problem.  I found a list in /var/lib/dpkg/info with the following:

```
metacity.prerm
mfc440cncupswrapper.conffiles
mfc440cncupswrapper.list
mfc440cncupswrapper.postrm
mfc440cncupswrapper.preinst
mfc440cncupswrapper.prerm
mfc440cnlpr.conffiles
mfc440cnlpr.list
mfc440cnlpr.postinst
mfc440cnlpr.postrm
mfc440cnlpr.prerm
mii-diag.list
```

I'm wondering if there is a way to manually take them away?? Or if it would work anyway?  This is because when I try to reinstall, I get error messages saying that they are already there in a corrupted form.

---

### Post by wantime on 2007-02-15
So I have my Brother MFC440CN now functioning well via usb using the drivers from the Brother Linux Drivers site.  In order to get them reinstalled I removed the package data relating to the MFC440CN in the directory /var/lib/dpkg/info (items listed above).

Simply opening first the LPR and then the CUPS  driver downolad files for debian based linux (its important to get them in that order due to the dependency of CUPS on LPR) ie, .deb files, led to a reinstall over whatever was wrong before it (I guess - because after that it worked!).

So now I will endeavour to get the network printing going.

---

