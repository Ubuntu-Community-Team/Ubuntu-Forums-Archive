---
title: "mplayer &amp; w32codecs on ppc -- help needed"
date: 2005-05-23
forum: Apple PPC Users
---

### Post by Brian McConnell on 2005-05-23
I'm hoping to get a full multimedia experience out of my killer Ubuntu OS. Basically, I need mplayer and it's mozilla plugin to allow me to view [trailers.apple.com](trailers.apple.com) in firefox.
I've installed mplayer and it's mozilla plugin from Synaptic/Hoary Universe and it doesn't work. I've also done the same with VLC and experienced the same non-working results. Each player will launch as a standalone app and play assorted file types with mixed results, but will not access the embedded content of web pages.
I'm guessing this is a result of the absence of w32codecs for ppc.
Here's my /etc/apt/sources.list in case anybody can suggest any worthwhile additions:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407)]/ hoary main restricted 


deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security universe 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe 

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
```

I'm using a PowerMac G5 with dual 1.8ghz processors. I'll take a working solution for either mplayer or vlc if anyone has one! Also should a G5 use mplayer-powerpc or mplayer-g4 installer?
I think once I can get this done, I just need to take care of getting transcode installed so I can do some video editing and capturing.

Any help is much appreciated and thanked for in advance  :wink:

---

### Post by Burgundavia on 2005-05-24
AFAIK, there are no w32codecs for PPC/amd64, due to the fact that they are 32 bit i386 binaries.

Corey

---

### Post by Brian McConnell on 2005-05-25
[QUOTE=Burgundavia]AFAIK, there are no w32codecs for PPC/amd64, due to the fact that they are 32 bit i386 binaries.

Corey[/QUOTE]


Right. But why is that VLC will play some .wmv's and some .mov's as standalone app and it shows as an installed and enabled plugin in firefox, but will not play embedded content from say, [trailers.apple.com](trailers.apple.com)?

---

### Post by craks on 2005-05-31
To play rmvb/rm, install realplayer for ppc linux version, if installed to /opt/RealPlayer

to compile mplayer by hand

./configure --with-librealdir=/opt/RealPlayer/codecs

that can play real media very well

---

