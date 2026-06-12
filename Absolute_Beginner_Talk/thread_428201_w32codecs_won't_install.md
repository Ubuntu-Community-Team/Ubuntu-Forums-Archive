---
title: "w32codecs won't install"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by MugenDraco on 2007-04-30
I have followed instructions elsewhere in the forums for installing w32codecs, but i keep getting the following error.

The following packages have unmet dependencies:
  w32codecs: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.4 is to be installed

The only libc6 I can find is version 2.3.6-0ubuntu20.4.  2.5-0ubuntu1 is nowhere to be found.  It seems like I've tried everything, but the w32codecs just will not install.

---

### Post by Sef on 2007-04-30
Have you read the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") page?

---

### Post by MugenDraco on 2007-04-30
I've tried everything on the Medibuntu page, but it still gives me the same error.  Ironically though, I just found out that MPlayer can play all my video files if I initiate it from command line.  Yet for some reason it will not play anything if I use the gui.

---

### Post by Sef on 2007-04-30
What version of Ubuntu are you using?

---

### Post by MugenDraco on 2007-04-30
6.06.  7.04 kept freezing on me, so I downgraded back.

---

### Post by PriceChild on 2007-04-30
Sounds to me like you are using a w32codecs made for a distribution other than the one you are using.

For example you are using w32codecs for Feisty on Edgy.

---

### Post by MugenDraco on 2007-04-30
No I specifically made sure I followed the directions for Dapper.

---

### Post by Najand on 2007-04-30
The package (for dapper) information is shown like:
> Package: w32codecs
Priority: optional
Section: libs
Installed-Size: 33580
Maintainer: The Medibuntu Team <medibuntu@sos-sts.com>
Architecture: i386
Version: 20061022-0medibuntu1
Replaces: libaviplay (<= 0.50-0.3), divx-codecs
Depends: libc6 (>= 2.3.4-1), libstdc++5 (>= 1:3.3.4-1)
Suggests: mplayer, gstreamer0.10-pitfdll
Conflicts: libaviplay (<= 0.50-0.3), divx-codecs, w32codecs-lite, qt6codecs
Filename: pool/dapper/non-free/i386/w32codecs_20061022-0medibuntu1_i386.deb
Size: 14254010
MD5sum: bc50f0d3da114674d786960424aa371e
SHA1: fbc7fa03ac044d6979384f45ba9ebc4cf7e1cf1f
SHA256: 61ecddb8e663d02657c7c370f978a35de821425973339935bd7267117c77b539
Description: Win32 codec binaries
 This package contains Win32 codec binaries, required for the
 decompression of video formats that have no open source
 alternative.
 .
 Homepage: [http://www4.mplayerhq.hu/](http://www4.mplayerhq.hu/)
 .
 This is in Medibuntu for it's non-free license.

So there is no need for libc6 2.3.4-1 when you have 2.3.6-0ubuntu20.4!
Can you post your /etc/apt/source.list here?

---

### Post by MugenDraco on 2007-04-30
ok here is my sources list.

-----------------------------------------------------------------------------------------------------------------------
#


deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

### Post by psusi on 2007-04-30
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

                                                                        ^^^^^^

You are trying to install the feisty w32codecs on edgy.

---

### Post by zvacet on 2007-04-30
Why don´t you just take this source list
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by aysiu on 2007-04-30
Get rid of the Feisty repositories (highlighted in bold): > **MugenDraco said:**
> ok here is my sources list.

-----------------------------------------------------------------------------------------------------------------------
```
#


**deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted**
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
[b]deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted[/b]
```

---

### Post by starcraft.man on 2007-04-30
If you want, easy solution is to use the [dapper ubuntuguide.org]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") repos. They are clean and I believe all the repos you need are there, just an option for ya.

Yours seem to be a mess, I don't understand how ya got Feisty repos mixed in with Dapper, musta been one of those autoconfig programs...

---

### Post by MugenDraco on 2007-05-01
ok.  removing the Feisty lines from my sources list worked somewhat.  the w32codecs package installed cleanly, but the gui still cannot play files.  they work from command line though.  the embedded mplayer in Firefox also works.  i suppose i can live without the gui.  it's just nice to have it.

---

### Post by Ziggy72 on 2007-05-01
Why don't you get the latest version of Automatix2 from [ http://www.getautomatix.com/]( http://www.getautomatix.com/). Make sure you get the correct version for your Ubuntu version and make sure that you also download the necessary gpg keys. Using Automatix2 you will be able to seamlessly download and install a great number of very useful programs (including the W32 codecs) without any hassle and fiddling around.

---

### Post by teddybairs1 on 2007-05-01
Why don't you give some of the other media players a try? I've got the Totem, Kaffeine, and Mplayer, as well as the third party realplayer just to see how they stack up against each other. So far, the best ones I've found for any playback is anything based on Xine (totem-xine, kaffeine, etc). I've never had any problems with the guis for these, and you can install kaffeine (which was written for KDE) into Ubuntu without having to go and pull down the entire Kubuntu desktop.

I haven't had a whole lot of luck with mplayer as a whole and keep going back to kaffeine, even under gnome.

---

### Post by MugenDraco on 2007-05-01
I've tried installing automatix, and for some reason ./configure and make do not work.  i've also tried using other players, but they all have the same problems as mplayer.  I can live with the way it is now, but thanx for the advice.

---

### Post by teddybairs1 on 2007-05-01
Dude, don't mess around with compiling when you don't have to. Download Automatix for Dapper from here:

[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-3.4-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-3.4-6.06dapper_i386.deb)

And just install it with the gdebi package installer, or with Kubuntu's package installer depending on which you have. This is the instruction wiki. I think you have to add one more repo to synaptic, but it gives you the line to cut and paste. Just follow the directions.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_i386.29)

Seriously, compiling is generally my absolute last resort because I'm so bad at it. So far, I haven't found but a few programs I wanted which weren't available somewhere precompiled and prepackaged as a .deb

---

### Post by PriceChild on 2007-05-02
Please don't use automatix. Read [uwiki]RestrictedFormats[/uwiki] which explains everything you need.

[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

