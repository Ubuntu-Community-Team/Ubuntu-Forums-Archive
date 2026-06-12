---
title: "Update manager can't connect to Internet/ Fresh Install"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by thecow on 2007-11-27
I use a proxy to connect to the internet, however I know the proxy works.  I am currently using it in firefox and firefox connects to the internet just fine.  So I tried to apply this proxy all around and share the goodness, I went to Preferences->Network Proxy and typed the proxy into there.  However when I try to run update-manager it says it can't connect and shows no new updates.  I know there are new updates as this is a fresh install.  And because it couldn't connect to the internet during installation it told me to 'investigate the matter' of updates when  Ubuntu finished installing.  When I first booted into Ubuntu I tried to download skype, and it gave me an error saying I didnt have 'libqt4-core' and I thought hm thats odd.  It also told me to add skype's URL to a list in some file in /etc/...etc  So I did but I noticed that every other URL was commented out with a comment above it saying 'Disabled in Installation because your didnt have internet' or something similar.  So how do I remedy this problem?

Thank you

---

### Post by angryfirelord on 2007-11-27
Post the output of:
```
sudo apt-get update
```
in a terminal.

---

### Post by thecow on 2007-11-27
brian@brian:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US               
Ign [http://download.skype.com](http://download.skype.com) stable Release                                  
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Reading package lists... Done

---

### Post by thecow on 2007-11-27
By the way the file that Skype had me add itself to is /etc/apt/sources.list

Seems to me it still thinks the cd-rom is in charge based off the terminal output and the first line in this file

The first few paraghs are :
"
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates universe
"

---

### Post by mcduck on 2007-11-27
Since you use proxy, the installer couldn't connect to internet during the install and therefore disabled the internet repositories in the sources.list file.

To get that fixed just go to System/Administration/Software Sources, and in the Ubuntu Software-tab enable everything (or leave the source code away, most likely you won't need it anyway..).

Then go to the Updates-tab and make sure that Important security updates and Recommended updates are also enabled.

If you want, you can also disable the install CD on the first tab. This way Ubuntu won't ask for the CD when you try to install stuff but instead just downloads the latest versions from the Internet repositories.

---

