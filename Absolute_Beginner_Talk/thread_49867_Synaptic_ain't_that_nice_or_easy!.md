---
title: "Synaptic ain't that nice or easy!"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by coolblue on 2005-07-18
OK I agree that operating Synaptic is easy.....but installing stuff with it is NOT.

I added Kubuntu CD and tried installing Kubuntu desktop but Synaptic will always fail in fetching certain KDE libs packages.

Also certain repos seem unusable (something like security.ubuntu...???).

And I'm not able to install dvd::rip...says it has dependencies and will not be installed?? And when I try to install transcode, it says it too has depends and will  never be installed!!! kde-sdk will also not install. I've had similar problems with many packages.

---

### Post by Knome_fan on 2005-07-18
Could you post your /etc/apt/sources.list?

It sounds like something got borked there.

---

### Post by damonw5 on 2005-07-18
[QUOTE=Knome_fan]Could you post your /etc/apt/sources.list?

It sounds like something got borked there.[/QUOTE]
 Hi coolblue,

One thing that might fix *some* of your problems would be to edit your /etc/apt/sources.list:

sudo gedit /etc/apt/souces.list

Whenever you see something like "http://us.archive.ubuntu.com/ubuntu" replace it with "http://archive.ubuntu.com/ubuntu" (In other words, remove the "us".) The US mirror is still having problems.

I agree with Knome_fan, seeing the contents of this file would help us a lot. Could you copy and paste it here?

---

### Post by Wolki on 2005-07-18
[QUOTE=coolblue]And I'm not able to install dvd::rip...says it has dependencies and will not be installed?? And when I try to install transcode, it says it too has depends and will  never be installed!!! kde-sdk will also not install. I've had similar problems with many packages.[/QUOTE]

Make sure that you don't have debian repositories enabled, like the ftp.nerim.net marillat repositories. They currently don't work with Ubuntu. Use backports-extras instead.

---

### Post by coolblue on 2005-07-18
[QUOTE=Wolki]Make sure that you don't have debian repositories enabled, like the ftp.nerim.net marillat repositories. They currently don't work with Ubuntu. Use backports-extras instead.[/QUOTE]
 Hi 
I've uninstalled Ubuntu and installed Kubuntu. And after a bit of reading, I edited my sources.list and heres the current setup:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050321)]/ hoary main restricted
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main
# deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

deb [http://kudos.berlios.de/hoary](http://kudos.berlios.de/hoary) ./
# deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main

deb [ftp://ftp.berlios.de/pub/gift-fasttrack](ftp://ftp.berlios.de/pub/gift-fasttrack) unstable main

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

deb [ftp://mirror.aarnet.edu.au/pub/java-linux/debian](ftp://mirror.aarnet.edu.au/pub/java-linux/debian) sarge non-free

deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
 
 ## Major bug fix updates produced after the final release of the
 ## distribution.
 # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse
 
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse
 
 deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./
 deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./
 
 deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./
 
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
 
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe restricted
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe restricted
 
# deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
# deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
 
 # Java - neustes SDK, JRE von Sun
# deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/
 
 # MPlayer, w32codecs, libdvdcss2, Transcode, Avidemux
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 
 # Bootspash Quelle
# deb [http://www.bootsplash.de/files/debian/](http://www.bootsplash.de/files/debian/) unstable main
 
 
 # unstable stuff
 
 # deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/i386/
 # deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/all/
 
 
 # super experimental
 
 # deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) unstable/
 # deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) experimental/
 
 
 # packages for multimedia and more, like mplayer
 
# deb [http://pessoal.onda.com.br/rjamorim/debian/](http://pessoal.onda.com.br/rjamorim/debian/) ./
# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
# deb [http://debian.xmixahlx.com/packages/unstable/](http://debian.xmixahlx.com/packages/unstable/) ./
 
 
 # more stuff
 
# deb [http://bulma.net/~daneel/debian/](http://bulma.net/~daneel/debian/) ./
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) unstable smurf
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) experimental smurf
 
# deb [http://www.stanchina.net/~flavio/debian/](http://www.stanchina.net/~flavio/debian/) ./

Yup its pretty long. Initially I enabled ALL repos and began having probs:)
Anyways Kynaptic feels better than Synaptic.
So what do u think abt my current sources.list?

Is it OK????

---

### Post by coolblue on 2005-07-18
Hi 
I've uninstalled Ubuntu and installed Kubuntu. And after a bit of reading, I edited my sources.list and heres the current setup:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050321)]/ hoary main restricted
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main
# deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

deb [http://kudos.berlios.de/hoary](http://kudos.berlios.de/hoary) ./
# deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main

deb [ftp://ftp.berlios.de/pub/gift-fasttrack](ftp://ftp.berlios.de/pub/gift-fasttrack) unstable main

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

deb [ftp://mirror.aarnet.edu.au/pub/java-linux/debian](ftp://mirror.aarnet.edu.au/pub/java-linux/debian) sarge non-free

deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
 
 ## Major bug fix updates produced after the final release of the
 ## distribution.
 # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted
 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe multiverse
 
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
 
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe multiverse
 
 deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./
 deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary/](http://www.mpe.mpg.de/~ach/kubuntu/hoary/) ./
 
 deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./
 
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
 
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe restricted
# deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe restricted
 
# deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
# deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
 
 # Java - neustes SDK, JRE von Sun
# deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/
 
 # MPlayer, w32codecs, libdvdcss2, Transcode, Avidemux
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 
 # Bootspash Quelle
# deb [http://www.bootsplash.de/files/debian/](http://www.bootsplash.de/files/debian/) unstable main
 
 
 # unstable stuff
 
 # deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/i386/
 # deb [http://www.lychnis.net/files/debian/](http://www.lychnis.net/files/debian/) unstable/all/
 
 
 # super experimental
 
 # deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) unstable/
 # deb [http://kitenet.net/~joey/debian/](http://kitenet.net/~joey/debian/) experimental/
 
 
 # packages for multimedia and more, like mplayer
 
# deb [http://pessoal.onda.com.br/rjamorim/debian/](http://pessoal.onda.com.br/rjamorim/debian/) ./
# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./
# deb [http://debian.xmixahlx.com/packages/unstable/](http://debian.xmixahlx.com/packages/unstable/) ./
 
 
 # more stuff
 
# deb [http://bulma.net/~daneel/debian/](http://bulma.net/~daneel/debian/) ./
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) unstable smurf
# deb [http://smurf.noris.de/code/debian/](http://smurf.noris.de/code/debian/) experimental smurf
 
# deb [http://www.stanchina.net/~flavio/debian/](http://www.stanchina.net/~flavio/debian/) ./

Yup its pretty long. Initially I enabled ALL repos and began having probs:)
Anyways Kynaptic feels better than Synaptic.
So what do u think abt my current sources.list?

Is it OK????

---

### Post by damonw5 on 2005-07-18
Yes, that is quite long! Anyway, here are some of the questionable (i.e. NON-Ubuntu/Kubuntu) repos that may be just for Debian that are enabled in your sources.list:

[QUOTE=coolblue]
deb [ftp://ftp.berlios.de/pub/gift-fasttrack](ftp://ftp.berlios.de/pub/gift-fasttrack) unstable main
...
deb [ftp://mirror.aarnet.edu.au/pub/java-linux/debian](ftp://mirror.aarnet.edu.au/pub/java-linux/debian) sarge non-free
...
 deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./
...
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
...
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 [/QUOTE]

If I were you I'd comment these out with a "#" if they are not ABSOLUTELY necessary.

---

### Post by Lord Illidan on 2005-07-18
Beware. Although Kynaptic has the KDE theme, Synaptic has far, far more functionality. I personally prefer KDE over Gnome but there are times when performance wins over looks, and that is the case with Kynaptic and Synaptic...

---

### Post by odin on 2005-07-20
when type apt-get update in some lines says "get" in others "hit" and others "ign"

is there anyone who can tell me what every of those mean?

thank's

---

### Post by Kyral on 2005-07-20
Honestly. I don't know, but it happens to me everytime yet it seems to work :D

---

### Post by doclivingston on 2005-07-20
Get = it downloaded the file
Hit = it didn't download the file, because your copy is already up to date
Ign = it didn't bother trying to download the file (this is usually for the "Release" files)

---

