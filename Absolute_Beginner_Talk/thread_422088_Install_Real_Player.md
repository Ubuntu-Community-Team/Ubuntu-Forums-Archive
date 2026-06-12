---
title: "Install Real Player?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2007-04-24
Hi,

 I am feeling more than a little stupid but I cannot see how to enable commercial repos and then install the Real Audio Real Player. I cannot see it commented out in etc/apt/sources.list where I simply planned to 'uncomment' it:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
```

 But I here there are then some issues with the Firefox plugin? I am keen not to install Automatix and do most of the work 'by hand' :-)

                Andrew

---

### Post by aktiwers on 2007-04-24
Did you remember to run:
```
sudo apt-get update
```

after saving your source.list?

---

### Post by aktiwers on 2007-04-24
Also you should remove those 4 linies from the end:

>  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

### Post by andrew.46 on 2007-04-24
Hi,

 Well I added the following:

```
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

 Which seemed promising, ran update / upgrade  but still no joy:

```
andrew@ilium:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

```

 My altered source list is now:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main


```

 I took out the 4 security lines as you suggested and added:
```
deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
```

 which is hopefully more correct?? I am operating with little knowledge in this area :( 

                   Andrew

---

### Post by andrew.46 on 2007-04-24
Hi,

 I will admit that it was getting all a little too messy :-) I visited  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) and produced a nice lean list and then installed automatix. I am now listening to streaming radio and my elegantly lean  source list is:

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/

# Ubuntu supported packages
deb http://au.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://au.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
deb http://au.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

#So I gave in and used Automatix :-)
deb http://www.getautomatix.com/apt feisty main
deb http://archive.canonical.com/ubuntu feisty-commercial main
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

```

 My good intentions are in ruins around me but Automatix does make things so much easier :-)

                            Andrew

---

### Post by nikkkko on 2007-04-25
Late in the day I know, but I installed RealPlayer in 30 seconds following this [ubuntu guide]("https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods").  I downloaded the .deb file and ran it from the desktop, (I'm using Kubuntu), reloaded Firefox and am now listening to the BBC.

---

### Post by andrew.46 on 2007-04-25
Hi,

 Well I have uninstalled Automatix2 and RealPlayer just to see if I could successfully install Real Player via Canonical's Commercial Repo under Feisty. I am aware that I can download a .deb or .bin file but this is simply a technical exercise :) 

 Now I could not do it. I have the following line in my /etc/apt/sources.list file:

```
# Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

 Which I understand should hold RealPlayer 10, Opera and a bunch of other stuff. I then run the following command:

```
andrew@ilium:~$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplay is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplay has no installation candidate

```

 Can someone duplicate what I have done and confirm that Real Player is *not* in the Canonical Commercial Repository? Or tell me that I am doing something really dumb :confused: 

         Thanks,

             Andrew

---

### Post by Delkster on 2007-04-25
> **andrew.46 said:**
> Can someone duplicate what I have done and confirm that Real Player is *not* in the Canonical Commercial Repository?
Without looking deeper, I'd assume there's nothing in the commercial repository yet. Things probably appear there after a while. I think it took a while after the Edgy release until the commercial repository was made available for it, too.

---

### Post by 007Bond on 2007-04-25
Get automatix solves all your problems.

---

### Post by Delkster on 2007-04-25
> **007Bond said:**
> Get automatix solves all your problems.

And possibly causes a bunch more later on.

The Edgy package of RealPlayer (from the edgy-commercial repository) seems to work ok also in Feisty. You can find the .deb package here: [http://archive.canonical.com/pool/main/r/realplay/](http://archive.canonical.com/pool/main/r/realplay/)

---

### Post by andrew.46 on 2007-04-25
Hi,

 Thanks for your reply:

> **Delkster said:**
> And possibly causes a bunch more later on. The Edgy package of RealPlayer (from the edgy-commercial repository) seems to work ok also in Feisty. You can find the .deb package here: [http://archive.canonical.com/pool/main/r/realplay/](http://archive.canonical.com/pool/main/r/realplay/)

 which comes like a fresh breath of calm and reason :).  I have downloaded and installed the .deb and remain without Automatix(2)  for the first time in my 4 month experience with Ubuntu.

 Do you know if there is a list or index to what is actually available in the Canonical 'Commercial' Repository for Feisty? I have left it active in my /etc/apt/sources.list as it seems to promise some decent software in the future at least.

                 Thanks again,

                        Andrew

PS Wooooooo hooooooooooo!!! 100 Posts!!!

---

### Post by Delkster on 2007-04-27
> **andrew.46 said:**
> Do you know if there is a list or index to what is actually available in the Canonical 'Commercial' Repository for Feisty? I have left it active in my /etc/apt/sources.list as it seems to promise some decent software in the future at least.

I assume they'll appear in Add/Remove Applications when you choose to display only "Third-party applications", but that's just assumption.

---

### Post by andrew.46 on 2007-04-27
Hi,

 I have had a bit of a look at the Canonical Software Repository idea and have found very little. [The only decent discussion of it ]("http://robitaille.wordpress.com/2007/01/06/the-canonical-commercial-repository-6-months-later/")refers to the Dapper project and it seemed a little dead in the water even back then.

 I might post in the forum elsewhere and see if I can dig up a little more info.

                         Andrew

---

### Post by Najand on 2007-04-27
Hmm, medibuntu repository have realplay; check out: [http://medibuntu.sos-sts.com]("http://medibuntu.sos-sts.com")

---

### Post by andrew.46 on 2007-04-27
Hi,

 I read your post with interest:

> **Najand said:**
> Hmm, medibuntu repository have realplay; check out: [http://medibuntu.sos-sts.com]("http://medibuntu.sos-sts.com")

 I had a look at the Medibuntu site and on the [packages page]("http://medibuntu.sos-sts.com/packages.php") I saw only the following non-free for Feisty:

[LIST=1]
[*]skype  1.3.0.53-1medibuntu2

[*] acroread-escript  7.0.9-0.0.ubuntu0.7.04+medibuntu2

[*]  acroread-plugins  7.0.9-0.0.ubuntu0.7.04+medibuntu2

[*] acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu2

[*] googleearth-data  4.0.2735.0-0medibuntu4

[*] googleearth  4.0.2735.0-0medibuntu4

[*] mozilla-acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu1

[*] mozilla-acroread  7.0.9-0.0.ubuntu0.7.04+medibuntu2

[*] w32codecs  20061022-0medibuntu1+build1

[*] skype-static  1.3.0.53-2medibuntu2
[/LIST]

 Is this page perhaps out of date?

                    Andrew

---

### Post by Najand on 2007-04-27
Oh, They have not made a patch for Feisty. Anyway, why don't you use the the "helix-player". It is under unverse repository and it is exactly the same thing (with green GUI instead of the realplayer blue GUI) including a plugin for mozilla. Even in [Realplayer]("http://www.real.com/linux") homepage it is also decribed that: "RealPlayer 10 for Linux is based on the open source Helix player". You can also download and install it directly from Real Homepage.

---

### Post by rggavubt on 2007-04-28
Install automatix using these steps at this web page for Ubuntu feisty :

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29)

Then install real player using automatix....much easier.

---

### Post by Delkster on 2007-04-29
> **andrew.46 said:**
> [The only decent discussion of it ]("http://robitaille.wordpress.com/2007/01/06/the-canonical-commercial-repository-6-months-later/")refers to the Dapper project
Like I said, there was a commercial repository for Edgy, but it was populated with packages only some time after the Edgy release.

If you look at [http://archive.canonical.com/dists/](http://archive.canonical.com/dists/), there's also a directory ready for repository information for feisty-commercial (note that the packages themselves would go to /pool rather than /dists).

I'd expect a feisty-commercial repository to appear and get some content in the near future, but of course I don't know any more of it than you do.

Anyway, I think there's nowadays little need for Automatix. Most codecs are more easily installed through Add/Remove Applications, Flash and Java can be installed that way, libdvdcss is only a link away (although you have to find the link -- but then, you also have to find out about Automatix somehow so it's not like it's really automatic either), etc. Those deb files that you have to download directly are also very easy to install nowadays. Thanks to GDebi, you only need to double-click on them just like you'd do to any file in order to open it.

The only real problem I can see at the moment is the Adobe Reader which some people may need regardless of free PDF viewers such as Evince. I don't suppose the free alternatives have support for form filling yet (correct me if I'm wrong -- I'm actually curious if they do), and I've also had some problems with Evince opening some PDF files. Now that it's gone from multiverse due to licensing issues (the license doesn't allow redistribution), it really isn't very easy to install except by finding and installing the Edgy packages through packages.ubuntu.com or from some third-party sources (which technically violate the license). Hopefully we can get some kind of a solution to that in the future (or, even better, have the free alternatives evolve into something so good that there's no need for Adobe's reader application).

---

