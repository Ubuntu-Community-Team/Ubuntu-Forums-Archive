---
title: "How To Use 'Alien -k' ; for which file ?"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-04
HI, 

I am big newbie and wish to install the last gaim.
I downloaded some version of gaim but they are not deb extension ...
I used alien -k gaim*.rpm and so on ...
but broken pipe.
  
Is there someone who know which file i should download redhat ?? or fedora or mandrake or .. ? and which way to install ?

thanks a lot

---

### Post by manicka on 2005-10-04
forget trying to alien anything

sudo apt-get install gaim

---

### Post by manicka on 2005-10-04
You may also have to add some extra repos 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by patrick295767 on 2005-10-05
Ok, I'll try tonight to let you know if these extra repos.. in my sources.list will enable installing the gaim v1.5

Thx a lot

---

### Post by patrick295767 on 2005-10-05
[QUOTE=manicka]You may also have to add some extra repos 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]


Hi, 

I just now added that extrarepositories to my sources.list
was it right to do so ??

I hope that it ll be working ... 

thx

---

### Post by Ampersand on 2005-10-05
Did you add 'http://ubuntuguide.org/#extrarepositories' to your sources.list, or make the changes explained in there?

Also, the ubuntu guide is slightly outdated. The mirrormax backports are no longer working, instead you need to add the line:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

to your sources.list.

---

### Post by Mustard on 2005-10-05
patrick, could you go to your /etc/apt/ directory and open up the sources.list file and then copy and paste your sources.list file into this thread?  Use the VBcode to format it correctly if you can, using the [noparse]```
<put your text between these two VBcode markers>
```[/noparse]

LIke this (this is my sources.list)...

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://au.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://au.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```

---

