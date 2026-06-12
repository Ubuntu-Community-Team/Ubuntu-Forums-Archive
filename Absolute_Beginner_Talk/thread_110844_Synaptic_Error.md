---
title: "Synaptic Error"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by ice60 on 2005-12-31
hi, i had a synaptic error a week or so ago so i changed the sources.list and it went, then afew days later i think it was AI posted his list so i copied and used that instead, adding a line i needed. that list has worked fine up until yesterday. i'm sure i haven't changed anything though so i don't understand what's causing the error.

here is the error i get when i run synaptic
```
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.skype.com stable/non-free Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.sourceforge.net binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.videolan.org sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```then when it loads it only shows installed apps (with the green boxes) i didn't scroll down the screen to fully check on that though. when i Reload it spends awhile updating from the internet and uses the "not installed (new in the repository)" icons next to most things which are usually iconless.

can you help me fix it please?

---

### Post by super on 2005-12-31
post your sources.list so i can have a look

---

### Post by ice60 on 2005-12-31
hi, super :) i thought i'd editted out Wine and Skype because i don't use them. should i uncomment backports too?

deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

#VLC Media Plyer
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

# Open Office 2 final
#deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

---

### Post by super on 2005-12-31
hmm...
every thing looks ok to me.
try running [FONT="Courier New"]sudo apt-get update[/FONT] from the terminal and see if that fixes anything.

if you are using ubuntu 5.10 (breezy) you should be ok after that.

---

### Post by ice60 on 2005-12-31
[QUOTE=super]hmm...
every thing looks ok to me.
try running [FONT="Courier New"]sudo apt-get update[/FONT] from the terminal and see if that fixes anything.

if you are using ubuntu 5.10 (breezy) you should be ok after that.[/QUOTE]
could it be a network error? or doesn't it use the network when it loads?

this is the same error i had before, when i update, everything does update, it takes awhile though. then everything shows as being new. then every time i open synaptic for the next 24 hours i get no errors but still everything shows as being new - with the star icons in the boxes they have next to them. then after 24 hours i get the error again.

the way i fixed it before was to try uncommenting one thing at a time. i still had to wait 24 each time to see if i got the error though. then when i saw AI's list i just used that instead and it was fine for the last week, then the errors again.

```
sudo apt-get update
```
worked fine, finished in afew seconds. when i do it after the error for the first time it seems like it's rebuilding the whole thing like it gets lost or something and takes alot longer.

BTW i'm using breezy

---

### Post by ice60 on 2006-01-12
is there anything i can do to fix this? it's a continuous loop - get the error, after which all it shows are the installed programs, update to repopulate the list, everything shows as new in the list, after afew days the "new" icons go then the next time i start synaptic the error shows again.

i don't think it's the sources list because i have totally changed it and it still happens. is the list being cleared by something every few days?

---

