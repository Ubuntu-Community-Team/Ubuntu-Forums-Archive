---
title: "Trusted Tutorial for Compiz-Fusion in 7.04?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-08-18
I have installed Ubuntu 7.04 and would like to test out Compiz-Fusion. I know that it's alpha/beta software, but I'd still like to take the risk. Trouble is I am VERY new to Ubuntu Linux and I'm looking for the right direction in which to be pointed. I've stumbled upon a few HOWTO's for Compiz-Fusion, but each one is a bit different and makes me question which is the best to go with. Here's the links I've considered using to install Compiz-Fusion:

[http://puttabutta.blogspot.com/search?updated-max=2007-06-26T20%3A34%3A00-04%3A00&max-results=10](http://puttabutta.blogspot.com/search?updated-max=2007-06-26T20%3A34%3A00-04%3A00&max-results=10)
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)


Could anyone tell me which best to use? If needed, my computer specs are as follows:

AMD Athlon 3000+
2.10GHz, 1.00GB of RAM
nVidia GeForce FX 5200 with 256RAM

---

### Post by dondad on 2007-08-19
I looked at most of those, but ended up doing a search for compiz in synaptic and installing from there. Worked fine for me doing it that way.

---

### Post by dswhite85 on 2007-08-19
I can install Compiz-Fusion through the Synaptic manager?

---

### Post by dondad on 2007-08-19
It shows up in my Synaptic as does emerald.

Here is my sources.list

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse


## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free

deb http://wine.budgetdedicated.com/apt feisty main


deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy


deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

#deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
```

---

### Post by Gausian on 2007-08-19
thats just regular compiz, not compiz-fusion

---

### Post by dondad on 2007-08-19
There are several compiz-fusion entries there. Maybe it is just regular compiz, but with a bunch of fusion stuff also?

---

### Post by 3rdalbum on 2007-08-19
If you joined the Ubuntu world at the same time that you joined the forums (March 2007) then Compiz Fusion is not something you should run. I've been using Ubuntu since Jan 2006 and I battled for hours trying to get it going properly. It's still unstable.

You'd be better off installing Beryl, which is faster, more stable, has better default options, and is just as impressive to Windows people :-)

[http://ubuntu-tutorials.com/2007/02/06/install-beryl-on-ubuntu-feisty-with-aiglx-for-nvidia-ubuntu-704/](http://ubuntu-tutorials.com/2007/02/06/install-beryl-on-ubuntu-feisty-with-aiglx-for-nvidia-ubuntu-704/)

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

Anyone know of a Feisty howto for ATI that includes installing XGL?

---

### Post by Gone fishing on 2007-08-19
I can't say thats my experience. I've got 2 PCs running 7.04 one runs Beryl the other Compiz-Fusion. I'd say that Compiz-Fusion is slightly more stable (can't really  remember it crashing or loosing the menu bars (apart from when running Penguin racer sometimes)) this happens occasionally with Beryl. Beryl does seem to have slightly better performance.

The softpedi instruction posted look about right.

---

### Post by Golyadkin on 2007-08-19
There is a [Compiz Fusion installation script]("http://ubuntuforums.org/showthread.php?t=508769") on this forum, but it didn't work for me. It gave compilation errors, but the script just goes on anyway. I don't really like having to compile this from source, aren't there any semi-stable point releases in .deb form?

---

### Post by Arthur Archnix on 2007-08-19
Your second link is the one that I would use. In all fairness though, I never got it working myself. I'm waiting for gutsy, which will probably include the first official release of compiz-fusion.

---

### Post by dondad on 2007-08-19
I joined in april of 2007 and have been running it ;-) It looks to me like it depends on what exact hardware you have, and maybe what you have also installed as well as the phase of the moon and your orientation in the Earth's magnetic field. Also, how comfortable you are with having things break and having to fix them. There were some upgrades yesterday and after applying them, compiz quit working. I took me an hour or so to get it fixed, but it seems to be working fine now. The only issue that I have is that the monitor will not power down when I run compiz. I use the icon to choose metacity when I leave the computer and it shuts down fine. I can re-enable compiz (with emerald) whenever I use the box.

I don't have a lot of experience with ubuntu, or linux and am having a lot of fun going up the learning curve. I do have around 30 years or so of computer experience, including assemply language programming, working with Windows since version 1.0 (yeah, I know that don't count ;-)) and I managed an oem embedded software group for about 8 years or so. I guess my point is that what someone should or should not be running is a case by case decision. Most everything I have tried to get going eventually works, sometimes with a lot of searching, reading, or getting help from the great people here on the forums. I am sure it helps that I have one of the Dell machines (xps 410) that comes with Ubuntu, although I am not using the version that came on it, but rather the one on the ubuntu download cd. I do know that the harware is ok for linux though and that helps in the quest.

---

### Post by sailor2001 on 2007-08-19
don't see where you would have any problems....click alt/f2 and type" compiz --replace

---

