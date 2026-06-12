---
title: "Flash Audio in Firefox"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2006-07-21
Youtube and Google video audio dont work.  The problem is that this is a fresh install of Ubuntu.  I went through the SPM and got the AOSS-OSS library and I have added that to the firefox redit thing I found under some thread.  I even launched firefox through the terminal with "aoss firefox."  Nothing works.

Not only that but the Youtube video seems to lock up every 3 secs even after it has finished buffering the video.  I have to manually pull the video along to get it to keep playing.  No such problem with Google video.

Also, I had quicktime movies playing , with audio, but without controls.  Now, the movie and controls show up for a brief flash of a second, then they disappear while the page loads.  And nothing plays. I downloaded some quicktime libraries with the SPM, but I dont really know whick one messed it up.

---

### Post by Cornbreadly on 2006-07-21
Not only that, but Firefox seems to crash alot right after visiting youtube.

---

### Post by crispy_420 on 2006-07-21
Did you try install something called esound for apt? That solved my sound with flash.

As far as Quicktime video, I have all codecs installed and they play fine. I think the ones you need are w32. I may be wrong about that though. For default player I use mplayer via the mplayer plugin for firefox. But in either case you will need to add some extra repos. I'm not on my Ubuntu system so I can't give you them but look for the PLF repos (search PLF in forums).

---

### Post by Uncle Spellbinder on 2006-07-22
I used/use [AUTOMATIX]("http://www.ubuntuforums.org/showthread.php?t=177646"). This *sources.list* has served me well:

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free

## Automatix Repositories
deb http://www.beerorkid.com/automatix/apt dapper main
```

My Firefox plugins are as such:

```
**Generated:** Sat Jul 22 2006 00:31:17 GMT-0400 (EDT)
**User Agent:** Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1b1) Gecko/20060721 BonEcho/2.0b1
**Build ID:** 2006072114

**Installed Plugins:** (9)
- Adobe Reader 7.0
- Google VLC multimedia plugin 1.0
- Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
- Java(TM) Plug-in 1.5.0_06-b05
- mplayerplug-in 3.17
- QuickTime Plug-in 6.0
- RealPlayer 9
- Shockwave Flash
- Windows Media Player Plugin
```

---

