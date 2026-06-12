---
title: "Complete repositories list"
date: 2005-02-07
forum: Apple PPC Users
---

### Post by Caesar on 2005-02-07
Hi all,
i'm trying to get a few updates via apt-get (libdvdcss2, win32codec and a few more) but my repositories list is missing somenthing.

Here my list:
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha powerpc Binary-1 (20050204)]/ unstable main restricted

deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe


deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse

##deb ftp://ftp.nerim.net/debian-marillat/ stable main
##deb ftp://ftp.nerim.net/debian-marillat/ unstable main
##deb ftp://ftp.nerim.net/debian-marillat/ testing main

``` 

I know that the debian-marillat repositories got the packages that i need but those severs are not working for me.... this is why i've disabled them.

Could someone post a complete depositories list-file to get those packages?


TIA

---

### Post by ralph_ubuntu on 2005-02-07
For (unstable) ppc versions of the packages found in the marillat repository try:
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/

w32codecs don't work on ppc though, so you won't find them and can't use them.

---

### Post by val1984 on 2005-02-07
Or you can use [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/)

---

### Post by Caesar on 2005-02-07
Thanks for your help.
I'm installing css libs for DVDs palyback right now.

Do you have any idea about additional audio and video codecs?
I've installed vlc trought Synaptic but i'm missing audio in all my DVDs, VCDs, .avi and .mov or .mp4 files.

---

### Post by ralph_ubuntu on 2005-02-07
Can't really help you with the codecs, but the mplayer deb from the repository I posted works quite well for me. Maybe give it a try.

---

### Post by Caesar on 2005-02-07
I'm just curious: why it told me that can't find a puclikey for "http://apt.cerkinfo.be/ unstable"?

---

### Post by Caesar on 2005-02-07
[QUOTE=ralph_ubuntu]For (unstable) ppc versions of the packages found in the marillat repository try:
deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) mplayer/
.[/QUOTE]

Ok, i'm gonna try mplayer too.
How to add that repository to source.list?

Adding these lines to source.list give me an error  ](*,) 
```
deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian
deb-src http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian
```

Thanks for your help :)

---

### Post by ralph_ubuntu on 2005-02-07
You forgot the mplayer/ and I don't think there is a deb-src repository.
Just copy and paste the line from here:
[http://debian.video.free.fr/](http://debian.video.free.fr/)

About the missing pubkey, hoary now uses gpg to authenticate packages. For more information take a look here:
[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)
(I don't know if there is a key for the site I posted though)

---

