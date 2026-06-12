---
title: "How to install kubuntu-desktop / kde-core"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by fatboysam on 2008-02-14
Hi,

Newbie here to Linux and Ubuntu. I have installed Ubuntu 7.10 and now want to install KDE.

Went to the following website, i.e: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) but really at a loss here.

I'm not sure what the steps are to install KDE on top of Ubuntu, i.e which packages and what dependencies are involved.

Would really appreciate a step by step on how to install KDE into Ubuntu.

Thanks.
fs.

---

### Post by emarkd on 2008-02-14
If you want the full Kubuntu desktop, just:

```
sudo apt-get install kubuntu-desktop
```

That'll get all of it.

---

### Post by fatboysam on 2008-02-14
Hi,

Thanks for the quick reply but I actually tried this command, i.e:

sudo apt-get install kubuntu-desktop

but received an error saying that the package kubuntu-desktop could not be found.

Where can I get this from so that I can install using sudo apt-get install kubuntu-desktop?

Thanks.
fs.

---

### Post by emarkd on 2008-02-14
apt-get downloads the software from the online repositories.  It's highly preferred that you use the software in the repositories instead of downloading stuff and installing it manually.  This is one place where Linux differs greatly from Windows.  Do you have internet access on the computer you ran that on?

---

### Post by fatboysam on 2008-02-15
Just ran the command: sudo apt-get install kubuntu-desktop and I am connected to the internet and received the following messages:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop

Any ideas?

---

### Post by p_quarles on 2008-02-15
Did you have a working internet connection when you installed the operating system? If you didn't, Ubuntu will disable fetching packages from online repositories, and limit itself to the boot CD.

Try running this:
```
cat /etc/apt/sources.list
```
My guess is that the output of that file will have a lot of lines beginning with "#." If you can post that output here, someone can help you repair it.

---

### Post by fatboysam on 2008-02-15
Here is the output of sources.list

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
#deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

---

### Post by p_quarles on 2008-02-15
Yeah, my guess was correct. The most reliable way to fix this is to edit that file:
```
gksudo gedit /etc/apt/sources.list
```
Once the file is open, remove the "#" symbol from each line that begins with etierh "deb" or "deb-src." Once you've done that, save and close the file, then update the package cache by running:
```
sudo apt-get update
```
The command you were having trouble with earlier should now work.

---

### Post by fatboysam on 2008-02-15
All good now with install of kubuntu-desktop but how does one start up KDE - nothing seems to have changed after install.

Is there something else I have to perform to actually start kde?

Thanks.
fs.

---

### Post by emarkd on 2008-02-15
On your login screen, click sessions and select kde from there.

---

### Post by p_quarles on 2008-02-15
At the login screen, look for the "Options" menu. In that, choose "Sessions," and you'll see selections for Gnome and KDE.

---

### Post by fatboysam on 2008-02-15
sorry - but where on the logon screen do I click on session?

FYI, I am running Ubuntu 7.10 on a MBP Pro through VMware Fusion.

ta.

---

### Post by fatboysam on 2008-02-16
hi, found options screen at bottom left on Login screen but when I selected "Session", KDE was not listed - any ideas?

fs.

---

