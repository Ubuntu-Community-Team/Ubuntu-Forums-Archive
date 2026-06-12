---
title: "Problems downloading updates using the software update tool"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Haydn on 2006-10-15
Hey,

I am experiencing problems similar to yours (at my best guess) and since there were no real responses to this with solutions, what may I ask did you do to resolve this issue?

What's happening for me is that I am receiving the notifications that updates are available fine. It will even list which updates are available. It stops short however of displaying the information in the changes tab - This is when I am using the built in software update tool. The main problem is presents when I select which updates to install and then try to 'install updates': the program will open up a 'downloading package files' window but will not ever progress in the downloads. What should I try to download these updates?
Is there a way to manually download them off the web?

Thanks in advance,
Haydn

---

### Post by Haydn on 2006-10-15
btw when I run "sudo apt-get update" in a terminal, the output is as follows:

sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Fetched 9645B in 6s (1593B/s)
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Haydn

---

### Post by ReaderRat on 2006-10-15
You may need to enable more repositories, so the software will be available to you.
Repositories - Adding Extra:
          [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by Haydn on 2006-10-15
The page you suggested contained the following info: (I'll let you know where the problems start.)

Adding Extra Repositories

To enable the extra repositories:

   1.

      Open System->Administration->Software Properties .
   2.

      Select Add
   3.

      To enable the Universe repository, check the Community Maintained (Universe) button.
      [Note] 	

      Adding this repository will mean that the majority of the Free Software universe will be available to install on your system. This software is supported by a carefully selected group of volunteers within the Ubuntu Community, but is not supported by the core Ubuntu development team and may not include security updates.
   4.

      To enable the Multiverse repository, check the Non-free (Multiverse) button.
      [Warning] 	

      Adding this repository will mean that software which has been classified as non-free will be available to install on your system. This software may not be permitted in some jurisdictions. When installing each package from this repository, you should verify that the laws of your country permit you to use it. Again, this software may not include security updates.
   5.

      Click Close to save your changes and exit.
   6.

      To apply your changes, select Reload. ****At this step I have the same problem as with the software update tool - nothing will even start downloading.

Thankyou again for your help,
:confused: Confused Haydn:confused:

---

### Post by Bigbluecat on 2006-10-15
The issue you are seeing is to do with the public key for Easyubuntu - you do have this installed don't you?

There is a mehtod to fix this on the forums. Have a look at the following thread:

[http://www.ubuntuforums.org/showthread.php?t=273888](http://www.ubuntuforums.org/showthread.php?t=273888)

I have to say that I tried it an it didn't work for me but then again I don't think this really causes any problems. I have no issue installing software so I have not pursued in any detail.

---

### Post by Haydn on 2006-10-15
Nope, this hasn't solved my problem yet. Is there any more info that I should be providing you with? :-k 

Haydn

---

### Post by NeoLithium on 2006-10-15
Try to disable the freecontrib repositories first.
```

sudo gedit /etc/apt/sources.list

**Add a # in front of the freecontrib repositories then save the file and exit.**

sudo apt-get update

sudo apt-get upgrade

```

---

### Post by Haydn on 2006-10-15
Thanks, this allowed me to download most of the updates etc. there are still some that weren't downloaded though and I received this error:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to 129.128.159.69:8080 (129.128.159.69), connection timed out

Hrm?!?

Haydn

---

### Post by NeoLithium on 2006-10-15
Can you copy and paste the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by Haydn on 2006-10-15
#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

You are awesome for following through w/ my problem neo. Thx a bunch!!:p

---

### Post by junglepeanut on 2006-10-16
Hmm, I looked into this a little, and checked that those repositories are good, they seem to be as I can follow the tree, but what it says it can't link to, are down as I can not link to those. 

Maybe you could try switching to a US server just for a period to see if that gets it working?

ps: I am a newbie and have no idea what I am talking about just followed links.

---

### Post by Haydn on 2006-10-16
Can you suggest some specific changes that I should make please? I've worked with linux a lot, but it has all been at university. I don't have the practical experience of working with it on my own. :confused:

---

### Post by junglepeanut on 2006-10-17
Here is my sources (except I changed all instances of edgy to dapper, but they should be the same for you now but with a us server.) I have no idea if this will work.
Just use what you need :)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## PLF
## Please report any bug on [https://launchpad.net/products/plf/+bugs](https://launchpad.net/products/plf/+bugs)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper-plf free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper-plf free non-free

##EasyCAM
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

##Canonical Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by epique on 2006-10-18
Hi i had this problem with easy ubuntu about half an hour ago and it seems to have worked for me ish altho not quite wright.

enter the following code into the terminal

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -


hope it works for you   btw it came from a french site maby that is why its not working perfectly

---

### Post by epique on 2006-10-18
sorry i put some furthe testing into it and altho it says that the items have been installed they have not. ill come back to you if i can correct this.

---

