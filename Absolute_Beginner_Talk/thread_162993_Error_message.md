---
title: "Error message"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by bluemarble on 2006-04-20
Hiya, everything was going well enough, but every time i open the package manager I get a error message that shows the following;

> W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

Any help in getting rid of the message would be great....

Bluemarble

---

### Post by trent dillman on 2006-04-20
I assume you used Automatix. :-p

Open your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```

Then, put a pound sign # at the beginning of each line that corresponds to the addresses given in the error message. Save the file, and use Synaptic to reload your sources.

---

### Post by bluemarble on 2006-04-20
When i enter ** gksudo gedit /etc/apt/sources.list** at the command line sources.list opens but there is nothing in there. So do I type it all from scratch and should there be code already there? if you know what i mean...:???:

---

### Post by trent dillman on 2006-04-20
Yeah, it should have something in there already. Check for typos, and use the terminal instead of the run prompt. With the terminal, you can type

'/e<TAB>/apt/so<TAB>'

and the shell should use autocompletion and fill the rest in!

Or, just open a terminal and copy/paste the following:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by bluemarble on 2006-04-20
just one pound sign or two, like the rest for example;

## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any revie
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by bluemarble on 2006-04-20
Well I went with one # and saved the source list and then reloaded through Synaptic... looked like all was going well but when it finished reloading i got a message saying;

Could not download all repository indexes

[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to ftp.free.fr:21 (1.0.0.0), connection timed out
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Release.gpg:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Release.gpg:) Could not connect to koti.mbnet.fi:80 (1.0.0.0), connection timed out
[http://theli.free.fr/packages/breezy/./Release.gpg:](http://theli.free.fr/packages/breezy/./Release.gpg:) Could not connect to theli.free.fr:80 (1.0.0.0), connection timed out

So all in all i have made some progress... i think:-k

---

### Post by trent dillman on 2006-04-20
Just comment out any that don't have Ubuntu domain names. Also, you might be having connection problems.

---

### Post by meborc on 2006-04-20
check the breezy guide in my sig for proper sources.list file... also how to enable universe/multiverse... :wink:

---

### Post by aktiwers on 2006-04-20
You can copy paste my list, if you want. 

```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## breezy-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./



# for IRSSI
#Then run apt-get update; apt-get install irssi
#deb http://www.davidpashley.com/debian/irssi-sarge/ ./
 

# BOINC packages for Ubuntu 5.10 "Breezy Badger"
deb     http://pkg-boinc.alioth.debian.org/ubuntu breezy universe
deb-src http://pkg-boinc.alioth.debian.org/ubuntu breezy universe

```

---

### Post by bluemarble on 2006-04-20
cheers peoples that did the trick....

where would i be without you...

---

