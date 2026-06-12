---
title: "Another wifi probem"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by fattysfinest on 2007-12-30
Hi,I hope this is as easy to solve as the last one.
I have an Acer travelmate 290 with a intel pro wireless lan 2100 3b mini pci (adarter rev 04) I running Ubuntu 7.04
i tried to get build essentias to run and i get the folowing
bb@ :~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also have this error È:ubuntu-restricted-extras
depenency problems
leaving unconfiguered
and
E: mstt corefonts:subprocess post installation script
returned error exit status (then a forward slash, for some reason this keyboard gives me a
 ` mark like this é when i hit the sash key)

thanks 
Brian

---

### Post by spiderbatdad on 2007-12-30
not sure but looks like you need to run```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

---

### Post by fattysfinest on 2007-12-30
Thanks for the quick response
I tried what you suggested and got the following
bb@ :~$ sudo apt-get update
Password:
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2) gutsy/main Translation-en_CA
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2) gutsy/restricted Translation-en_CA
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_CA
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_CA
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_CA
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_CA
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Fetched 4B in 3s (1B/s)
Reading package lists... Done
bb@ :~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev ndiswrapper-utils-1.9
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
E: Sub-process /usr/bin/dpkg returned an error code (1)
bb@ :~$ 

Any thoughts
brian

---

### Post by erfahren on 2007-12-30
you need to add the medibuntu repository for the fonts (I think) or else you need the Canonical enabled

see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

(make sure you do the part where it says to add the key)

it looks like you already have build-essential installed (I think it's installed by default on Gutsy)

---

### Post by MrFSL on 2007-12-30
NO I disagree. **fattysfinest** has the package - but it is failing to install correctly. Specifically during installation the config script is failing.

Do you have a proxy at your location?

My suggestion is to remove this failed attempt at msttcorefonts:
```
sudo apt-get --purge remove msttcorefonts
``` 

Then run an update/upgrade:```
sudo apt-get update
sudo apt-get upgrade
```

Probably wouldn't hurt to drop all your cached debs:
```
sudo apt-get clean
```

And then check your sources/repos (SEE advise given above) and then try to install the fonts again:
```
sudo apt-get install msttcorefonts
```

Hope this helps.

---

### Post by fattysfinest on 2007-12-30
thanks for the reply, i tried to do the above in the  termina but when it asks for my password nothing happens, the keyboard seems dead except enter

---

### Post by MrFSL on 2007-12-30
you wont see anything when you type your password

---

### Post by fattysfinest on 2007-12-31
duh, I thought the curser woud move, thanks
ok I did as you suggested and got the following
bb@ :~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  msttcorefonts
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 35.0kB of archives.
After unpacking, 213kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse msttcorefonts 1.8ubuntu1 [35.0kB]
Fetched 35.0kB in 0s (41.8kB/s) 
Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 133962 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.8ubuntu1_all.deb) ...
Setting up msttcorefonts (1.8ubuntu1) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

any thoughts

---

### Post by MrFSL on 2007-12-31
I don't understand. Did you get any error from these three lines?
```
sudo apt-get --purge remove msttcorefonts
sudo apt-get update
sudo apt-get upgrade

```

Please also post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by MrFSL on 2007-12-31
and...
> duh, I thought the curser woud move, thanksI think the idea is that if the cursor moved, a person could look over your shoulder and know the number of characters in your password - making it that much easier to guess. Of course someone looking over your shoulder could probably see you typing or at least count key presses... never quite saw the reason for it myself.....:confused:

---

### Post by fattysfinest on 2007-12-31
bb@ :~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe #Added by software-properties

bb@ :~$ 

I got the othere posted error when i tried to install fonts
thanks for your help on this

---

### Post by erfahren on 2007-12-31
I think MrFSL asked this before, but are you connecting through a proxy or do you have a direct internet connection?

If you connect directly try going to System -> Preferences -> NetworkProxy and make sure that you have Direct connection to the Internet selected.

---

### Post by erfahren on 2007-12-31
also do this:
```

cp /etc/apt/sources.list /etc/apt/sources.list_back

```
open up your current sources.list
```

sudo gedit /etc/apt/sources.list

```
replace everything in it with what is below:
```

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

## Uncomment deb-src if you wish to download the source packages

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
# deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free

```
save and add the key for Medibuntu
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
After that you also might try going to Software Sources and in the "Download From" drop-down select "Other" and then "Select Best Server".

**Then do the steps [MrFSL laid out in his post](http://ubuntuforums.org/showpost.php?p=4041433&postcount=5) again.**

hopefully all that will do it!

---

### Post by MrFSL on 2007-12-31
Thank you **erfahren** I agree.

---

### Post by fattysfinest on 2008-01-01
ok I followed what erfahren posted, when I get to
Save and add the key to medibuntu
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
do i add this to the sources list and save again, then follow MrFSL`s post
thank you
brian

---

### Post by erfahren on 2008-01-01
> **fattysfinest said:**
> ok I followed what erfahren posted, when I get to
Save and add the key to medibuntu
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
do i add this to the sources list and save again, then follow MrFSL`s post
thank you
brian
no... don't add that to the sources.list 

-  just enter that line into the terminal (it will just come back with a "[OK]" )

then go to his steps

---

### Post by fattysfinest on 2008-01-01
By the way I did the Direct not proxy thing, it was on auto
I get this error on the first step
bb@ :~$ cp /etc/apt/sources.list /etc/apt/sources.list_back
cp: cannot create regular file `/etc/apt/sources.list_back': Permission denied
bb@ :~$ 

I did manage to reload msfonts agian but maybe not correctly as i skipped the above step

---

### Post by erfahren on 2008-01-01
> **fattysfinest said:**
> By the way I did the Direct not proxy thing, it was on auto
I get this error on the first step
bb@ :~$ cp /etc/apt/sources.list /etc/apt/sources.list_back
cp: cannot create regular file `/etc/apt/sources.list_back': Permission denied
bb@ :~$ 

- my fault. I needed to put "sudo" in front of that. That line just would've made a back up copy (cp) of the sources.list you had before you edited it, but it's not a critical system file anyway and your old one was a little messy.

> 
I did manage to reload msfonts agian but maybe not correctly as i skipped the above step

It might have worked. did you get any kind of error message when installing the fonts like you did before? 

If it worked the fonts should show up in the font selection of OpenOffice (or whatever) - short list of some of them [here](http://packages.debian.org/unstable/x11/msttcorefonts)


you could try installing something else through the terminal to make sure it works. Are there any other packages you can think of that you wanted?

---

### Post by fattysfinest on 2008-01-01
Ok Now I seem to have the font problem fixed. I feel like I've done something even though you did all the work!
I still don't have any wireless conection, Do I need to find a driver for my intel 2100? And how do I do this?
Thank you for all the help, I would be lost without you, (like i'm not lost now)
Also when i changed my software source to" best one" the one it selected didn't work so I switched it back to Canada.

---

