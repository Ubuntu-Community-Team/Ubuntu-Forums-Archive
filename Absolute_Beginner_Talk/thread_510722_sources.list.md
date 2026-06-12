---
title: "sources.list"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-07-26
I think I screwed up my sources.list while adding sources to it. I don't think I'm getting all the major updates. I'm not sure. Can someone please take a quick look at it to make sure I'm not missing anything major? Thanks.

---

### Post by Armman on 2007-07-26
or if it is easier, just post your source list so I can compare it with mine.

---

### Post by RomeReactor on 2007-07-26
Hi. Your sources.list looks OK. What updates are you missing? This is mine, by the way:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/

---

### Post by Armman on 2007-07-26
I'm not sure, I was just playing around with my source list when trying to install Compiz-Fusion and then I decided the Effects weren't worth it and got rid of the sources. Not sure if I deleted some major sources so I just wanted to makes sure. Thanks for the reply.

---

### Post by starcraft.man on 2007-07-26
> **Armman said:**
> I'm not sure, I was just playing around with my source list when trying to install Compiz-Fusion and then I decided the Effects weren't worth it and got rid of the sources. Not sure if I deleted some major sources so I just wanted to makes sure. Thanks for the reply.

Just a note but if you ever find you completely messed up your list it's easy to restore it with the one on Ubuntu guide (make sure it's the same version). Oh and if you'd like to know more about the sources list and installing, feel free to check my guide (blue link in sig). A better solution is to always keep a back up of your stable version (before modifying).

All the best :).

---

### Post by Armman on 2007-07-26
Ok I rember why I was worried about my source.list. This came up when I did sudo apt-get update 

W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: You may want to run apt-get update to correct these problems

Is this major?
 
BTW Thanks for the tip starcraft.man

---

### Post by starcraft.man on 2007-07-26
> **Armman said:**
> Ok I rember why I was worried about my source.list. This came up when I did sudo apt-get update 

W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: You may want to run apt-get update to correct these problems

Easy to fix, you just have to add the authentication key. I'd give you the quick answer (an easy command) but I think it's easier and better explained if you just push the blue link in my sig and pay attention to the Authentication Keys section. Look to the index if you just want skip to right section, but I recommend reading it front to back I assume your new and it will be informative.

The URL to get the key you need is:

[http://packages.dfreer.org/7572013D.gpg]("http://packages.dfreer.org/7572013D.gpg")

Once ya read the section, you'll know where to use that. Oh and I explain both the GUI and CLI way, pick your favourite.

---

### Post by Armman on 2007-07-26
Thanks starcraftman your guide came in handy and I successfully added the key.

---

### Post by starcraft.man on 2007-07-26
> **Armman said:**
> Thanks starcraftman your guide came in handy and I successfully added the key.

Np. If you have friends having trouble feel free to point them to it. :)

---

### Post by wolfen69 on 2007-07-27
or, if your lazy: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)    will create a brand new sources.list ready to go.

---

