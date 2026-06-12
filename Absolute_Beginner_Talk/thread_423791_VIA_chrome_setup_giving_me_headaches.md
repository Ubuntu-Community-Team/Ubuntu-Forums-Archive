---
title: "VIA chrome setup giving me headaches"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Artyrussell on 2007-04-26
The good news is I'm accessing this forum from my new install of Feisty dual booting with XP. Installation was a dream, I expected to face many problems with networking, getting online but it all worked out of the box. 

My first problem came when I installed a game and it ran super slow, a quick search online found that it was probebly the graphics driver not install properly. I found this page [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) that addressed my graphics chipset. I'm mildly computer literate in a very basic sense (build my own computers, been using computers since dos etc) but it looked pretty daunting... I had a go anyway.

At the "openChrome 2D driver compilation" I stalled where it said "make" it said something about not finding the make file or such like?

I skipped to "openChrome and 3D" and got down to sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/

It said - cp : cannot start '*.ko' : no such file or directory

So I'm stuck?

I've a dual AMD with 2GB ram and 2 hard disks, I'm using the 32bit version of Ubuntu

---

### Post by father of 2 sons on 2007-04-26
Hello,

I had some difficulty as well with installing via unichrome drivers as well.  It looks like you may be having be receiving error messages due to missing some dependancies.  While running edgy,  I used this how-to: 

[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

It looks like this how-to has a unichrome specific forum/thread going, so you might be able to get more specific support on the page as well.

Hope this helps.

---

### Post by Seisen on 2007-04-26
Did you follow the guide exactly, I had no trouble getting it to work? Did you use apt-get or aptitude to install the files..

---

### Post by Artyrussell on 2007-04-26
> **Seisen said:**
> Did you follow the guide exactly, I had no trouble getting it to work? Did you use apt-get or aptitude to install the files.. I'll look up apt-get or aptitude as I don't know what they are? I cut and pasted into the terminal program (I guessed this was what to do as they didn't say and I'm a rock bottom Linux beginner).

Thanks for that other page father of 2 sons, I followed it but again problem almost imediately at
sudo apt-get build-dep xserver-xorg-video-via

it said the following

 E: Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_source_Sources - open (2 No such file or directory)

---

### Post by Seisen on 2007-04-26
Did you enable the universe and multiverse repo's?

---

### Post by Artyrussell on 2007-04-26
> **Seisen said:**
> Did you enable the universe and multiverse repo's?

If you mean under "software sources" that universe and multiverse repo's are ticked, then yes they are.

---

### Post by Artyrussell on 2007-04-26
I've googled apt-get and aptitude and the levels of assumed knowledge seem daunting. I really don't see what I'm doing wrong following those guides?

What does that error (below) mean?

E: Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_source_Sources - open (2 No such file or directory)

---

### Post by Seisen on 2007-04-26
Try removing "gb" from all your repo's here is what my source list looks like.

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Listen
# deb http://theli.free.fr/packages/ feisty listen

deb http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe

##Pixma iP1500 Drivers
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```

I tried adding "us" (because I live in the United States) back when I was using Edgy and I had problem getting the repos to work.

---

