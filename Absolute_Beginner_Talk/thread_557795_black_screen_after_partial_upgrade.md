---
title: "black screen after partial upgrade"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by jannevanhecke on 2007-09-23
i reinstalled festy and i have to upgrade to gutsy.
But when its upgraded and i restart the pc, i only see the status bar of ubuntu and then a black screen.
What can i do?

---

### Post by alienexplorers on 2007-09-23
Do you have the proper video drivers installed if not install them.  If you can boot in recovery mode up to a terminal you might want to try > sudo dpkg-configure xserver-xorg

---

### Post by jannevanhecke on 2007-09-23
i cnat boot in recovery mode

---

### Post by alienexplorers on 2007-09-23
Do you have more than one Kernel in your grub listing.  If so try an older Kernel.

---

### Post by jannevanhecke on 2007-09-23
i have kernel 2.6.22-12-generic
2.6.22-12-generic (recovery
2.6.22-7-generic
2.6.22-7-generic(recovery

everytime i have the black screen

---

### Post by PmDematagoda on 2007-09-23
> **jannevanhecke said:**
> i have kernel 2.6.22-12-generic
2.6.22-12-generic (recovery
2.6.22-7-generic
2.6.22-7-generic(recovery

everytime i have the black screen

Even with Recovery mode? It doesn't bring you to a terminal?

---

### Post by regomodo on 2007-09-23
i had exactly the same thing. Something about a kernel panic and not able to mount the filesystem.

For some reason it was trying to boot 2.6.20 but i had the option for 2.6.22 so i selected it and it worked

---

### Post by jannevanhecke on 2007-09-23
recovery stops with
root@ubuntu: #

---

### Post by alienexplorers on 2007-09-23
You know that is not good.  Really looking like a reinstall.

Can you get into the grub loader.  If so when it starts for you to
select a kernel hit e.  Edit  /boot/grub/menu.lst and look for a line like this:
> title		Ubuntu, kernel 2.6.15-29-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

Remove the word quiet and save. reboot and see if any error messages come up during boot.

---

### Post by jannevanhecke on 2007-09-23
ok i wil reinstall then.
But i already reinstalled yesterday and i had the same problems.Is it better i dont do any upgrades then?
thanks for thehelp

---

### Post by PmDematagoda on 2007-09-23
> **jannevanhecke said:**
> ok i wil reinstall then.
But i already reinstalled yesterday and i had the same problems.Is it better i dont do any upgrades then?
thanks for thehelp

Are you installing Feisty then upgrading it to Gutsy? If so that is a very bad idea, atleast until Gutsy is properly released. If you want Gutsy right now, download the latest Test release and install it, no upgrading and less worries:).

---

### Post by jannevanhecke on 2007-09-23
or should i install gutsy ?

---

### Post by PmDematagoda on 2007-09-23
> **jannevanhecke said:**
> or should i install gutsy ?

If you want Gutsy and not Feisty then it will be easier to install Gutsy directly than through an upgrade.

But a word of caution, Gutsy is still in testing, so you have to expect problems from it.

Why do you want Gutsy anyway?

---

### Post by jannevanhecke on 2007-09-23
i dont want gutsy but when i install feisty it always askes to do an upgrade

---

### Post by PmDematagoda on 2007-09-23
> **jannevanhecke said:**
> i dont want gutsy but when i install feisty it always askes to do an upgrade

It asks you to do a "Partial Upgrade", directly after install?

---

### Post by jannevanhecke on 2007-09-23
yes it does, so what do i do then?

---

### Post by PmDematagoda on 2007-09-23
Post what you get in your sources.list file. Using:-

```
sudo gedit /etc/apt/sources.list
```

In your newly installed Feisty.

---

### Post by jannevanhecke on 2007-09-23
ok  i will, but he is reinstalling now...

---

### Post by jannevanhecke on 2007-09-23
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070627)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070627)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by jannevanhecke on 2007-09-23
nobody?

---

### Post by PmDematagoda on 2007-09-23
Are you sure you are trying to install Feisty, because from your sources file I see that it is in fact Gutsy, not Feisty.

From where did you get the .iso file?

---

### Post by alienexplorers on 2007-09-23
When you boot and your screen goes back are you able to enter ctrl-alt-F1.  If so when you get to the login prompt login.  Next type:
> sudo dpkg-reconfigure xserver-xorg
Once done enter ctrl-alt-F7
reboot

---

### Post by jannevanhecke on 2007-09-23
i got it from the official ubuntu download site

---

### Post by PmDematagoda on 2007-09-23
Hmm, could you give me the exact link?

---

### Post by jannevanhecke on 2007-09-23
[http://nl.releases.ubuntu.com/7.04/](http://nl.releases.ubuntu.com/7.04/)

---

### Post by PmDematagoda on 2007-09-23
Here is my Sources file:-
```

#deb http://repository.debuntu.org/ feisty multiverse
#deb-src http://repository.debuntu.org/ feisty multiverse
#deb http://repoubuntusoftware.info/ feisty all

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu feisty-updates universe

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty universe


deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main



#AUTOMATIX REPOS END
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ feisty-security main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ feisty-security main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main multiverse restricted
# deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb http://getswiftfox.com/builds/debian unstable non-free
```

---

### Post by jannevanhecke on 2007-09-23
can i do something about that?

---

### Post by PmDematagoda on 2007-09-23
> **jannevanhecke said:**
> can i do something about that?

Hmm, like what alienexplorers is trying to do, first we try and revive the GUI, and if that doesn't work then we try something else. So it's your call alienexplorers, I'll chip in when possible.

---

### Post by alienexplorers on 2007-09-23
Don't use that repo list.  It contains links to Automatix which is a piece of junk.

---

### Post by alienexplorers on 2007-09-23
Try doing what was posted in post # 22.

---

### Post by PmDematagoda on 2007-09-23
> **alienexplorers said:**
> Don't use that repo list.  It contains links to Automatix which is a piece of junk.

Well, I have used Automatix and it works properly for me. So let's just try and help the person really in need of help right now.:)

---

### Post by jannevanhecke on 2007-09-23
ok ill try
thanks

---

