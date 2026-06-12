---
title: "[SOLVED] Installing Firefox on Kubuntu"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by manzeli on 2008-04-05
Hello.
I'm new to Linux world and just finished to install Kubuntu on my computer. I tried to install firefox but get the following message:
sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

Any help will be appreciated.

---

### Post by mgranet on 2008-04-05
What does your /etc/apt/sources.list file look like? You might be trying to pull an old version of firefox out of an old repo, perhaps.

---

### Post by bubba_169 on 2008-04-05
If you are using Kubuntu Hardy you may need to install the package firefox-3.0 instead, so:

```
sudo apt-get install firefox-3.0
```

---

### Post by manzeli on 2008-04-05
> **mgranet said:**
> What does your /etc/apt/sources.list file look like? You might be trying to pull an old version of firefox out of an old repo, perhaps.

All the lines at this file are commented out...

---

### Post by manzeli on 2008-04-05
> **bubba_169 said:**
> If you are using Kubuntu Hardy you may need to install the package firefox-3.0 instead, so:

```
sudo apt-get install firefox-3.0
```

No luck...
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firefox-3.0

BTW, 
I downloaded firefox-2.0.0.13.tar.gz, tar it to a temporary location and then tried: sudo apt-get install firefox

---

### Post by bubba_169 on 2008-04-05
If you have no sources you can get no software :)

Uncomment the deb lines based on what software you want. Firefox should just be in the main supported repository. Dont forget to 'sudo apt-get update' after changing your sources...

---

### Post by mgranet on 2008-04-05
> **manzeli said:**
> All the lines at this file are commented out...

Uncomment your lines so they look like this:
```
# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted

```
You may have to edit as root.

---

### Post by manzeli on 2008-04-05
I updated the sources.list file but could not install.
I did sudo apt-get update and get the following:
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by bubba_169 on 2008-04-05
Are you connected to the internet when you try this? What version of ubuntu are you using?

---

### Post by paydaydaddy on 2008-04-05
Have you tried installing with adept package manager. I use Kubuntu 7.10 and all I did was enable all repositories and adept loaded firefox right up for me. If you need details, just ask.

---

### Post by stomakmonkee on 2008-04-05
If all of those lines are commented out, then when you installed Kubuntu there was no internet access.  Further proof is that when you tried to reach these repositories after install you couldn't access them.  If you have internet connectivity in your home and your box was connected to an active connection during install, are you sure that your network card is supported?

---

### Post by manzeli on 2008-04-06
I have internet connection... I am using it right now... :-)
I am using Kubuntu version 7.10
I have uncommented the servers at sources.list file as was suggested by one of the replies but still no solution.
It's very :confused: .

---

### Post by bubba_169 on 2008-04-06
Please post a copy of your sources.list file so we can see whats going on. Dont worry it contains no personal information...

---

### Post by manzeli on 2008-04-06
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by kingofthenoobs on 2008-04-07
I've been having the same problems as you earlier today, finally fixed it.
GO to K > System > Adept Manager

after it loads up, on the top left click "Adept" and then "manage repositories."
under "Kubuntu software", I 'x'ed the first 4 boxes, then went to the "updates" tab and 'x'ed the first 2 (might be unrelated but I figured it was a good thing).

After that, "close" and "Fetch Updates". Then Search: firefox, scroll down to #2, "firefox-3.0" and install it. Then "accept changes." 

Close Adept Manager and go to K > Internet > Firefox. 

\\:D/ happy day!! :guitar:

now go to [www.youtube.com](www.youtube.com) or any streaming site and be able to watch the weirdo's you so sourly missed when using crappy Konqueror. 8) Hey nut-nobs! ):P

This is my first time using Linux so I just listed exactly what I did to make sure it shows up for you, but possibly firefox 3.0 shows up in search without even configuring repository. I actually installed Ubuntu and wanted to download KDE desktop but none of the 3 methods were even close to working for some reason so I just gave up and installed Kubuntu in full. Now I'm thinking it wasn't the best idea. :-k

Super noob, away! :KS

---

### Post by bubba_169 on 2008-04-07
Your sources.list looks fine to me? Can you post the exact output from the terminal when you try 'sudo apt-get update' with this sources.list (make sure your connected to the net before you try it). Before, your output looked like you were missing encryption keys (gpg's) for the repositories but did you just copy mgranets sources.list over your own?

---

### Post by manzeli on 2008-04-07
I checked with mgranets sources.list and got the same problem. I tried to reinstall Kubunu but no improvement!
The Kubuntu is installed over a VMWare desktop and I am using a router to connect to the Internet.

The version is:
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

The output for sudo apt-get update is:
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
.
.
.

---

### Post by kingofthenoobs on 2008-04-08
i have the same vers 7.10 as you... just installed as well. why not try what i did, it worked. who cares if its not through terminal..8-[

---

### Post by manzeli on 2008-04-08
> **kingofthenoobs said:**
> i have the same vers 7.10 as you... just installed as well. why not try what i did, it worked. who cares if its not through terminal..8-[


It's basically what we are doing via the terminal. I did tried what you suggested but the problem still exist. I'm very frustrated.

---

### Post by paydaydaddy on 2008-04-08
At the risk of expounding on the obvious, try bringing up the Kmenu and look under "internet" to see if firefox is listed there. When I first loaded it on my machine I thought it didn't load, but it was in the list under "internet". I realize that it is a longshot, but take a look all the same.

---

### Post by aysiu on 2008-04-08
One of these threads should help you:
[[SOLVED] Can not download any updates or packages.](http://ubuntuforums.org/showthread.php?t=403953)
[[SOLVED] Cannot make my repositories work](http://ubuntuforums.org/showthread.php?t=308102)

To all those who have tried to help so far, Firefox is not in the menus and is not installed. The repositories are in the sources.list, but they cannot be researched because the domain names cannot be resolved.

---

### Post by manzeli on 2008-04-08
I managed to solve the problem. 
I edited the sources.list file and changed the servers URL by adding il. at the beginning (instead of the original server - [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
I wrote -
[http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe)
The system start working but it was not stable!

At that point I suspected a DNS problem. I changed the DNS setting to different server and the problem SOLVED!

Although I did not find firefox 3, I did installed firefox 2.

Thank you all.

---

