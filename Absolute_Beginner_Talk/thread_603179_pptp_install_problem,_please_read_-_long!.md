---
title: "pptp install problem, please read - long!"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by helane on 2007-11-04
corefile posted exactly the same problem as i have:

> 
apt-get install pptp-linux needs cd???
apt-get install pptp-linux

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
pptp-linux
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/93.9kB of archives.
After unpacking 217kB of additional disk space will be used.
Media change: please insert the disc labeled
'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter

Why do I need to put in the CD? I don't have the dang thing any more, and whats the point anyway it should download what ever it needs. This seems broke to me.


fdoving responded:
> 
take a look at the /etc/apt/sources.list file.. uncomment the "deb http://archive..." lines
and add # in front of "deb cdrom... " lines.

then do apt-get update;apt-get isntall pptp-linux


the problem - i do not understand what to do in the sources.list file. i opened it with text editor and see:

>  deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


i am completely lost. please help...

helane.

---

### Post by TeaSwigger on 2007-11-04
Hm ok. What I suggest is that you use Synaptic Package Manager. In there you can bring up an options window for repositories. Repositories are where ubuntu looks for things to download. In those options you'll see where you can select to remove the CD as a source for packages. You can select to add other useful sources as well such as security updates, "backports" for updated apps and so on. It will safely change that sources.list file for you accordingly.

When you've made the changes it will ask you to update the listings, so ok that. Then you can install what you need in Synaptic trouble free.

Then you can take your time and learn this sources.list file. It's very easy to do once you figure things out. :)

---

### Post by TeaSwigger on 2007-11-04
After looking over that file, I'm lost. 

Is this a new install of ubuntu 7.10 'Gutsy Gibbon' from the live CD? Do you have a working internet connection on this ubuntu computer?

---

### Post by helane on 2007-11-04
it is 7.10. just installed from CD a few weeks ago and everything works perfect including internet. 

i just tried to disable cd as you said from synaptic - and it worked. i installed network-manager-pptp... then installed pptpconfig

got pptp going but it will not add the server... i put the data as requested

failed to open etc/pptpconfig/lock inormation entered has not been saved 


i feel like an idiot... which i am not :)

any ideas?

i am not new to set ups but new to linux and just following instrucions - in this case i have no idea what am i doing..

helane.

---

### Post by TeaSwigger on 2007-11-04
Glad to hear it worked and that ubuntu works great for you. :)

Whereas I know something about sources.list and repositories etc, you have me on vpn. lol Don't know the first thing on it! In case the right folks aren't looking in here I would suggest starting a thread like "help installing VPN?" or some such. Luck :)

---

### Post by helane on 2007-11-05
ok... few hours later...

IT WORKS! vpn works... thank you for your help and mainly encouragement.

now qorking on something else - after i disabled CD in the synaptics - java does not work! :( tried to put cd back. tried to install java... having problems though... 

helane.

---

### Post by SpiritIsReality on 2007-11-07
howdy
for Java
click the ? icon in top panel, or click System -> Help and Support.
In the help window that opens, enter java in the search box, and press enter key.
trails

---

### Post by helane on 2008-03-09
fixed everything a couple of months later.

thanks for your help. figured it all out but was away for a while so was not posting...

---

