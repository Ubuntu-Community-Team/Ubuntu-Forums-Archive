---
title: "where is mplayer"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by OU812 on 2007-04-14
Hello. I edited /etc/apt/sources.list

```
# 
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

But when I search for mplayer in synaptic, I only get kmplayer. I read this wiki

[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

but the editing instructions all refer to dapper. I have 6.10 server installed. I also notice some of my entries start with us. What can I do? Thanks.

john

---

### Post by bashologist on 2007-04-14
Try this:
```
sudo apt-get install mplayer
```

Optionally when it's installed you can setup the codecs with this:
```
if which mplayer; then cd /tmp; if wget [noparse]http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2[/noparse]; then tar -xvjf all-20061022.tar.bz2; sudo mkdir /usr/lib/win32; sudo mv all-20061022/* /usr/lib/win32/; fi; else echo "install mplayer first"; fi
```

---

### Post by speeves on 2007-04-14
Try adding multiverse to your sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

Then running:

sudo apt-get update; apt-cache search mplayer

It should now show up.  I always search the Ubuntu Package Search page when I have problems finding one:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

(I use the Firefox search engine, because I do this so much :P ).

---

### Post by OU812 on 2007-04-14
Thanks! I didn't know that the edgy multiverse repos in my sources.list were different than the ones that you provided. I am installing mplayer as we speak. Also, thanks for  the ubuntu packages link. Very handy. And bookmarked.

john

---

