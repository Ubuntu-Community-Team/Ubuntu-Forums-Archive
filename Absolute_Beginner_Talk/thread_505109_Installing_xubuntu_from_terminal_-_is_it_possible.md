---
title: "Installing xubuntu from terminal - is it possible?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-19
Here's the story:

I very recently learned that Ubuntu Feisty won't run without at least 256MB RAM. This old junkie computer doesn't have that, and so I was recommended to install xubuntu.

The only computer I have that is able to burn CDs died about 4-5 months ago (to everyone's lack of surprise, it was using windows...)...so burning the alternate CD is out of the question - I only have 123 MB RAM or so. Very depressing...but it works.

I'm currently using Knoppix 3.8, and my sources.list is shown below.

> # /etc/apt/sources.list for Knoppix
# If you want to do a "full upgrade", you should first
# upgrade the Packages from Debian/unstable (KDE & Co.)
# before doing a (dist-)upgrade for Debian/testing.
#
# See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
# CDROMs are managed through the apt-cdrom tool.

# Security updates for "stable"
deb [http://security.debian.org](http://security.debian.org) stable/updates main contrib non-free
deb [http://security.debian.org](http://security.debian.org) testing/updates main contrib non-free

# Stable
deb [http://ftp.de.debian.org/pub/debian](http://ftp.de.debian.org/pub/debian) stable main contrib non-free
deb [http://ftp.de.debian.org/pub/debian-non-US](http://ftp.de.debian.org/pub/debian-non-US) stable/non-US main contrib non-free

# Stable Sources
#deb-src [http://ftp.de.debian.org/pub/debian](http://ftp.de.debian.org/pub/debian) stable main contrib non-free
#deb-src [http://ftp.de.debian.org/pub/debian-non-US](http://ftp.de.debian.org/pub/debian-non-US) stable/non-US main contribnon-free

# Testing
deb [http://ftp.de.debian.org/pub/debian](http://ftp.de.debian.org/pub/debian) testing main contrib non-free
deb [http://ftp.de.debian.org/pub/debian-non-US](http://ftp.de.debian.org/pub/debian-non-US) testing/non-US main contrib non-free

# Testing Sources
#deb-src [http://ftp.de.debian.org/pub/debian](http://ftp.de.debian.org/pub/debian) testing main contrib non-free
#deb-src [http://ftp.de.debian.org/pub/debian-non-US](http://ftp.de.debian.org/pub/debian-non-US) testing/non-US main contrib non-free

# Unstable
deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) unstable main contrib non-free
deb [http://ftp.de.debian.org/debian-non-US](http://ftp.de.debian.org/debian-non-US) unstable/non-US main contrib non-free

# Unstable Sources
#deb-src [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) unstable main contrib non-free
#deb-src [http://ftp.de.debian.org/debian-non-US](http://ftp.de.debian.org/debian-non-US) unstable/non-US main contrib non-free

# Experimental
deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) ../project/experimental main contrib non-free

# Experimental Sources
#deb-src [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) ../project/experimental main contrib non-free

# ndiswrapper source
deb   [http://ndiswrapper.sourceforge.net/debian](http://ndiswrapper.sourceforge.net/debian) ./

# NX stuff
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) experimental main
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) unstable main

# ndiswrapper
# deb   [http://rigtorp.se/debian](http://rigtorp.se/debian) unstable/
# deb-src       [http://rigtorp.se/debian](http://rigtorp.se/debian) unstable/

# Blades Repository (pppoeconf & co)
# deb [http://people.debian.org/~blade/testing](http://people.debian.org/~blade/testing) ./
# deb-src [http://people.debian.org/~blade/testing](http://people.debian.org/~blade/testing) ./

# deb cdrom:[Debian GNU/Linux 2.2 r3 _Potato_ - Official i386 Binary-1 (20010427)]/ unstable contrib main non-US/contrib non-US/main

# Knoppix special packages resource at LinuxTag HQ
# deb [http://developer.linuxtag.net/knoppix](http://developer.linuxtag.net/knoppix) ./
# deb-src [http://developer.linuxtag.net/knoppix](http://developer.linuxtag.net/knoppix) ./

# deb [http://snapshot.debian.net/archive](http://snapshot.debian.net/archive) pool gcc
# deb-src [http://snapshot.debian.net/archive](http://snapshot.debian.net/archive) pool gcc



What would I need to add to be able to install xubuntu and whatever else is required using apt-get?

If, that is, I can even do so...I'm guessing I'd need to install xcfe as well...

I'm hoping for xubuntu to become the main environment I use (no Knoppix, it's just temporary). Is there any specific way I go about doing that, or will simply installing it work?

All these questions assume that it's even possible, and so I'm hoping it's not a 3 word answer (No, not possible).

---

### Post by Seisen on 2007-07-19
You can try changing your source list to ubuntu repo's but I have no idea if this will break your system. If this borks your system do you have a way to install knoppix back on your computer?

---

### Post by ARandomKid on 2007-07-19
> **Seisen said:**
> You can try changing your source list to ubuntu repo's but I have no idea if this will break your system. If this borks your system do you have a way to install knoppix back on your computer?

Yup, I've got the old install CD which installed Knoppix 3.8, which is what I'm using now.

Don't worry, I'm rather used to ubuntu exploding (I do things that don't wanna work,  accidentally uninstall important stuff...that type of thing...rather often :P Only my own fault, though...)

---

### Post by wolfen69 on 2007-07-19
you want this info   [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Seisen on 2007-07-19
Then I say go ahead and try it and if it breaks at least you can reinstall knoppix. By the way do you live in the U.S.?

---

### Post by wolfen69 on 2007-07-19
i just did my first succesful micro(8MB iso) install from the server. and added basic gnome, firefox . talk about fast!  i kinda like the idea of "building" ubuntu from the ground up.

---

### Post by ARandomKid on 2007-07-19
Alright. I've got a list of general ubuntu fiesty repos (no idea why...), so I'll pu tthose in place of what's there and try it.

What certain packages should I install?

---

### Post by Seisen on 2007-07-19
```
x-window-system-core xfce4 xfce4-terminal thunar firefox
```

---

### Post by ARandomKid on 2007-07-19
> **Seisen said:**
> ```
x-window-system-core xfce4 xfce4-terminal thunar firefox
```

Alright, thanks. Now if I could just find that stupid list...I had it...

---

### Post by Seisen on 2007-07-19
```
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
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

```

To add the PLF repository's gpg key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

---

### Post by wolfen69 on 2007-07-19
just follow the instructions on the link i gave. 

here's how i did it:

after base install:
```
sudo nano /etc/apt/sources.list
```
then
uncomment # before any line that starts with deb. save by ctrl. x, y, enter.
```
sudo apt-get update
```
```
sudo apt-get install gnome-core xorg gdm
```

you'll be able to boot to a gui after install. just remember that almost nothing is installed after doing this. basic gnome. im doing it on a spare drive right now.
edit: you can also substitute gnome for any other desktop environment. see link.

---

### Post by ARandomKid on 2007-07-19
> **wolfen69 said:**
> just follow the instructions on the link i gave. 

here's how i did it:

after base install:
```
sudo nano /etc/apt/sources.list
```
then
uncomment # before any line that starts with deb. save by ctrl. x, y, enter.
```
sudo apt-get update
```
```
sudo apt-get install gnome-core xorg gdm
```

you'll be able to boot to a gui after install. just remember that almost nothing is installed after doing this. basic gnome. im doing it on a spare drive right now.
edit: you can also substitute gnome for any other desktop environment. see link.

Only problem is that I can't burn an iso to a CD.

I have no working burner.

---

### Post by Seisen on 2007-07-20
So did changing your source list to feisty actually work or did it break your system.

---

### Post by ugm6hr on 2007-07-20
> **ARandomKid said:**
> Only problem is that I can't burn an iso to a CD.

I have no working burner.

Can you boot from USB on that machine?  If so - a minimal install is a possibility, with subsequent xubuntu-desktop (as per minimal install instructions).

Post #2 in [http://ubuntuforums.org/showthread.php?t=453922](http://ubuntuforums.org/showthread.php?t=453922) explains how to create a Ubuntu installation USB stick (but requires Windows access :(  and a 32MB USB stick)

I have tried this with the mini iso linked from psychocats ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

---

