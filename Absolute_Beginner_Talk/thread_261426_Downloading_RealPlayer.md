---
title: "Downloading RealPlayer"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Monika on 2006-09-20
Ok, this will sound very stupid, but where do I download realplayer from? I can only find an rpm on their website.
I've checked the instructions on [https://help.ubuntu.com/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html) but the address they give ([ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb)) just tells me there is no such directory.
I've done google searches and all and I just cannot find a realplayer .bin or .deb file for installation :(

---

### Post by elpuerco on 2006-09-20
[http://www.real.com/linux?pcode=rn&am](http://www.real.com/linux?pcode=rn&am)

---

### Post by X.Cyclop on 2006-09-20
[Add extra repos]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") and type:
```
sudo apt-get update
sudo apt-get install realplay
```

;)

---

### Post by Monika on 2006-09-20
Sorry, but neither of those work :( I'm using Breezy btw, don't know if that matters.

The first link brings me to where I was before - it only has a link to an rpm package download.

Using apt-get (or synaptic) on the other hand doesn't resolve the problem either. There is no 'realplay' package for Breezy, there is only 'realplayer' and the realplayer package is broken. It opens an installer which is supposed to download a *.bin file I think and then gives me an error message saying that I've not downloaded the file (or at least that it cannot find the file in the folder I chose).

---

### Post by elpuerco on 2006-09-20
If you click on the photo or the download button it will download a .bin file

---

### Post by Perfect Storm on 2006-09-20
the post above you follow the link then change the word dapper out with breezy.

Or better yet go to : [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to get a list for your soucelist.

Then 
```
sudo aptitude update
sudo aptitude install realplay
```

But you'll be better off with mplayer IMO.

---

### Post by elpuerco on 2006-09-20
AI, that source list creator link it bleedin marvlus!

I shall make use of that 

Thnx

:D :D :D :D

---

### Post by Monika on 2006-09-20
My sources.list file looks like this:

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

#############Ubuntu Breezy##############
deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

#############Ubuntu Security##############
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


#---------------------------Non_Ubuntu------------------------------
###############Kadu########################
deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) breezy main


And I have not been able to locate a package called 'realplay' in synaptic, only 'realplayer' which is broken.

As for the link - thanks, I was using Galeon and Galeon was not displaying the picture (or the link behind the picture). In firefox the picture appeared and I've downloaded the bin file.

---

