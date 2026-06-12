---
title: "apt-get Web Proxy and libdvdcss"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by pbobby on 2005-08-11
Couple of things

1. How can I make apt-get aware of my site proxy server? I've been using Synaptic Package Manager with no problems but would like to get the command line version working.


2. I was following the instructions to getting mplayer working inside Firefox, and one of the steps is "How to Install DVD playback capability" (from the ubuntu starter guide)

The file to search for is libdvdcss2 and it's nowhere on any of the repositories.

Yep I've added the repositories per the steps in the Starter Guide

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=pbobby]
2. I was following the instructions to getting mplayer working inside Firefox, and one of the steps is "How to Install DVD playback capability" (from the ubuntu starter guide)

The file to search for is libdvdcss2 and it's nowhere on any of the repositories.

Yep I've added the repositories per the steps in the Starter Guide[/QUOTE]


Its in the backports repo. Did you add that one?

---

### Post by odin on 2005-08-12
[QUOTE=pbobby]Couple of things

1. How can I make apt-get aware of my site proxy server? I've been using Synaptic Package Manager with no problems but would like to get the command line version working.


2. I was following the instructions to getting mplayer working inside Firefox, and one of the steps is "How to Install DVD playback capability" (from the ubuntu starter guide)

The file to search for is libdvdcss2 and it's nowhere on any of the repositories.

Yep I've added the repositories per the steps in the Starter Guide[/QUOTE]

For your proxy thing just do:

vi /etc/apt/apt.conf.d/proxy 

and type:

Acquire::http::Proxy "http://proxy_IP: proxy_port";

and that should make it work.

---

### Post by pbobby on 2005-08-12
Well the text in the beginners guide does not appear to work for me.

For example

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

I had to remove the 'us' in order for it to work.

And for that reason I'm unsure if any of the other URLs are accurate.

I'm still trying..

---

### Post by pbobby on 2005-08-12
Okay this is just so frustrating.

Here is my sources.list
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

When I open Synaptic Package Manager I get

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory) 

At the command line I have the following in /etc/apt/apt.conf.d/proxy

> Acquire::http::Proxy "http://192.168.146.35:80"; 

And when I type "apt-get update" from the command line all I get are attempts to connect to my proxy server but no updates :(

I have gotten Synaptic to work using the pre-made repositories, and even multiverse/universe to the pre-made repositories, but lordy I can't get any of these others to work.

---

