---
title: "apt-get problem"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2006-01-18
here is waht I get when I try to update

hc:smile: :smile: 

andy108@heis:~$ sudo apt-get install updates
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package updates
andy108@heis:~$

---

### Post by Sef on 2006-01-18
> andy108@heis:~$ sudo apt-get install updates

Try this:

Sudo apt-get update

---

### Post by mcduck on 2006-01-18
Could you post your sources.list here? I think you have problem with that.. At least the line 'http://archive.ubuntu.com breezy/universe Packages' should be like 'http://fi.archive.ubuntu.com/ubuntu breezy universe', without a slash.

You could also create a nice new sources.list with [Source-O-Matic]("http://www.ubuntulinux.nl/source-o-matic"). That would most likely solve your problems.

By the way, the commands to update your system is 'sudo apt-get update' to load information of what packages are available and installed, and after that 'sudo apt-get upgrade' to download and install updates. 'sudo apt-get install updates' would try to install a package called 'updates'..

---

### Post by Hotchilli on 2006-01-18
can't find list but will try 

gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

this is info from what was suggested inlast post I thibk??

hc:smile: :smile:

---

### Post by Hotchilli on 2006-01-18
here we go

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by Hotchilli on 2006-01-18
while I am in apt-get I also want to install kubuntu and uninstall ubuntu

thanks

hc:smile: :smile:

---

### Post by Sef on 2006-01-18
> while I am in apt-get I also want to install kubuntu and uninstall ubuntu

To install Kubuntu:

sudo apt-get install kubuntu-desktop

To uninstall ubuntu:

sudo apt-get remove (package name) --purge

Note: you still may have some Gnome packages left after the uninstall

---

### Post by mcduck on 2006-01-18
Well, the original problem sure is just that instead of updating your system the command you used tries to install some package called 'updates'. I already posted the proper way to update your system. (sudo apt-get update && sudo apt-get upgrade)

For some reason you seem to have most of repostiories commented out in your sources.list.. Is there a reason for that? You might want to enable those to get most out of your Ubuntu. Either use the link in my previos post to create a new custom sources.list, or try this one:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

To install KDE, run 'sudo apt-get install kubuntu-desktop'. I suppose that to remove Gnome after you have KDE running you could 'sudo apt-get remove ubuntu-desktop'.

---

### Post by Hotchilli on 2006-01-18
many thanks for all your posts

hc:smile: :smile:

---

### Post by Hotchilli on 2006-01-18
so would the source list change for a kubuntu install instead of unbuntu
write kubuntu?

thanks

:smile: :smile:

---

### Post by mcduck on 2006-01-18
[QUOTE=Hotchilli]so would the source list change for a kubuntu install instead of unbuntu
write kubuntu?

thanks

:smile: :smile:[/QUOTE]
no, there is no need for anything like that. Ubuntu and Kubuntu are the same, with the same repositories. Only difference is the window manager and applications installed. You can even have both, or add Xubuntu (XFCE4) and Fluxbox and IceWM too if you want :D

edit: if you have many desktops installed, you can choose wich one to use in the login screen, just click the 'sesions' button.

---

### Post by Hotchilli on 2006-01-18
woo thanks mcduck.

this forum rocks :smile: :smile: :smile:

---

### Post by mcduck on 2006-01-18
No problem, and you're right about this forum. It must be the only one where you can actually ask something and get answers instead of insults :D

---

### Post by Hotchilli on 2006-01-18
heres what I did not expect put mcducks file inplace

andy108@heis:~$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package kubuntu-desktop
andy108@heis:~$

---

### Post by mcduck on 2006-01-18
[QUOTE=Hotchilli]heres what I did not expect put mcducks file inplace

andy108@heis:~$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
.
.
.
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package kubuntu-desktop
andy108@heis:~$[/QUOTE]oh yeah, you need to run 'sudo apt-get update' first, so that apt-get knows what you have installed and what's available in the repositories. So try that first, and then try instaling Kubuntu again..

---

### Post by Hotchilli on 2006-01-18
well I am impressed with KDE the blue sort of hits you with brightness 
hmm but the defaults and proramms that were installed in gnome such as tor and
privoxy are not there do they need to be reinstalled in kde.

thanks for all your help

hc:smile: :smile: 
i

---

### Post by mcduck on 2006-01-18
I'm glad thing worked for you.

You don't need to reinstall any programs, as they are already installed on your computer. They just aren't in KDE's menus. You can still start them from terminal with programs name, and I suppose there must be some way to add things to KDE's menu like the Applications Menu Editor in Gnome. You could ask in Kubuntu forum about that, I have no idea as I've never liked KDE myself.

---

### Post by Hotchilli on 2006-01-19
Thanks for your feedback mcduck

KDE its for me a lttle bouncey its ok the layout is more 
different and the colour's are soert of cheerful.

loking for synaptic in kde?:smile: :smile:

---

### Post by mcduck on 2006-01-19
I bet it's called Kynaptic or something in KDE. :D But running 'sudo synaptic' from terminal should work if you haven't uninstalled ubuntu-desktop yet.

---

### Post by Hotchilli on 2006-01-19
thanks for that mcduck.

I will take a look and see I could keep gnome its ok up to know
just want to overload the syayem got two kernals on startup
now

well I am justwondering about postfix seen a good guide
at [http://flurdy.com/docs/postfix/#soft](http://flurdy.com/docs/postfix/#soft)

what would be the effect of unistalling gome in the shert term/long term do you 
think.


hc:smile: :smile:

---

### Post by mcduck on 2006-01-19
uninstalling gnome? You'd have to install it again when you start to miss it ;)

Seriously, it's no problem, but if you aren't low on disk space there's no reason to uninstall it.

You can also uninstall older kernels, if the new one is working fine.

---

