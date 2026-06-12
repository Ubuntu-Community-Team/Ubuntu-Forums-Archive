---
title: "gstreamer8.0-lame doesn't seem to exist anymore"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by timchater on 2006-08-20
Hello. Sorry to be once again raising the issue of ripping a CD to MP3 (discussed extensively elsewhere, with an explanation at [http://help.ubuntu.com/community/CDRipping](http://help.ubuntu.com/community/CDRipping))...

I recently installed the 64-bit version of Ubuntu 6.06, and have been thwarted in my attempt to encode MP3 files usind Sound Juicer. The reason, I think, is that it can't find the gstreamer0.8-lame package:

```
tim@ubu-ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame
```

Any ideas anyone? This package doesn't appear in Synaptic either. Has it been withdrawn? If so, what are the alternatives?

---

### Post by Perfect Storm on 2006-08-20
Did you enable universe/multiverse in your sourcelist?

---

### Post by timchater on 2006-08-20
> Did you enable universe/multiverse in your sourcelist?

Yes...

---

### Post by Perfect Storm on 2006-08-20
Tried updating your sourcelist first?
```
sudo apt-get update
```

How's your sourcelist looks like?
```
cat /etc/apt/sources.list
```


otherwise you can download it here:
[http://packages.ubuntu.com/dapper/libs/gstreamer0.8-lame](http://packages.ubuntu.com/dapper/libs/gstreamer0.8-lame)

---

### Post by timchater on 2006-08-20
It still wouldn't work with the updated source list after I'd updated it, but the download link fixed the problem, and now it appears in Synaptic.

Thank you!

Soucelist is as follows, by the way:
```
tim@ubu-ubuntu:/home$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main
```

---

### Post by Perfect Storm on 2006-08-20
ah, you need the unoverse/multiverse to add in your list:

```
sudo nano /etc/apt/sources.list
```

add:

[b]# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
[/b]

save and exit.
```
sudo apt-get update
```

---

### Post by timchater on 2006-08-20
Thank you very much.

---

### Post by Perfect Storm on 2006-08-20
My pleasure ^_^

---

