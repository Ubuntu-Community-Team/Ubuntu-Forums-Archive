---
title: "Some Problems (7.10 64 Bit)"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by xdwmx on 2007-10-18
I just downloaded and freshly installed Ubuntu 7.10 final (64 Bit Edition) onto my Acer Aspire laptop. From the Live CD I managed to boot to a GUI and the install went OK. However, after restarting the system I was not greeted with Ubuntu's 'loading bar', instead, all I saw was an empty black screen until the login window appeared and I was able to log in.

I have an 'AMD Turion 64 X2 TL52' processor and an 'ATI Mobility Radeon X1300' graphics card.

My laptop has a screen resolution of 1280x800, but Ubuntu only allows me 1024x768. When I use the Restricted Drivers Manager I try to enable 'ATI accelerated graphics driver'. But I get the error;

```

The software source for the package

 xorg-driver-fglrx

 is not enabled.

```

So I do as I did in 7.04 to get my graphics card working, by running the following;

```

sudo apt-get install xorg-driver-fglrx

```

But to no avail, I get the following error;

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

```

What next? How can I get the loading bar to show at boot, and how can I run at full screen resolution.

This also happened with Ubuntu 7.10 RC, at 32 and 64 bit.

Thanks.

---

### Post by skymera on 2007-10-18
sudo apt-get update
sudo apt-get upgrade

then try

---

### Post by xdwmx on 2007-10-18
Already tried that and still getting the same error.

---

### Post by skymera on 2007-10-18
can you post your sources.list?

could be helpful

---

### Post by xdwmx on 2007-10-18
Where would I find that file?

---

### Post by skymera on 2007-10-18
sorry should have said

sudo gedit /etc/apt/sources.list

---

### Post by Paul820 on 2007-10-18
Have you enabled restricted packages in system->administration->software sources ?

---

### Post by xdwmx on 2007-10-18
Is this it?

```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Paul820 on 2007-10-18
All your sources are comented out. You need to take the # off the beginning of the lines where the web address is.

---

### Post by Lord_Dicranius on 2007-10-18
I don't think uncommenting them will do anything for him...
> Line commented out by installer because it failed to verify

**EDIT**
I stand corrected.  I thought that it was one of those things that was set temporarily.  After some research, I've found I was wrong :)

---

### Post by Paul820 on 2007-10-18
Either the servers are having trouble with the gutsy rush or s/he wasn't connected to the internet when s/he installed gutsy. Either way, they still need uncommenting if any updates or packages need downloading.

---

### Post by Lord_Dicranius on 2007-10-18
You posted that just as I edited my other reply correcting myself :-)

---

