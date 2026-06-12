---
title: "new installation of feisty - plenty of problems"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by KuruJ on 2007-08-30
The first time I installed feisty, everything was working except i was having trouble with my ati video card........i tried a lot of things out from posts on forums regarding this problem, but none of it worked for me. So i reinstalled ubuntu hoping that i might be able to get it working if i start from scratch again..........but its just giving more issues now

right now my biggest problem is that i am not able to get any update packages

"sudo apt-get update" returns a long list of errors and fails in the form:
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/multiverse Translation-en_CA           
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA      
  Could not resolve 'archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'fr.archive.ubuntu.com'
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) Could not resolve 'fr.archive.ubuntu.com'
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2) Could not resolve 'fr.archive.ubuntu.com'

your help is very much appreciated. 
thanks.
kuru

---

### Post by dca on 2007-08-30
Looks like you're not connected to the Internet....

---

### Post by KuruJ on 2007-08-30
thanks.....thought bout that but thought it should be ok since i am able to use the browser.....not too computer savvy, as u must be able to tell.  guess there must be some proxies i have to set/configure eh.....well thanks, i will try some stuff out

---

### Post by jspangler on 2007-08-30
Could you post the output of your aptitude sources list? To do that following the following instructions.

1. Click Applications > Accessories > Terminal.

A box will come up. 

2. Type into this box the following:

```
cat /etc/apt/sources.list
```

3. Select the output with your mouse and go to Edit > Copy.

I hope that wasn't too simple for you :-)

---

### Post by KuruJ on 2007-08-30
hey...here u go....
when i was playing around with ubuntu yesterday it was at home.....but today am at work trying to get the video card to work......i am coop student so they let me just play around :)........alright i am pretty sure i am connected to the internet....i am able to surf the net......and i did set the network proxy......how to i check for sure that it is a connection issue?


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty
# main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse


deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main multiverse

---

### Post by jspangler on 2007-08-30
If you are able to surf the Internet there should be no problem with the internet connection. Your repository list looks good. It's possible that the port used by apt-get isn't open where you are. I don't know which port it uses, but you might want to talk to the network manager?

---

### Post by asmoore82 on 2007-08-30
> **KuruJ said:**
> The first time I installed feisty, everything was working except i was having trouble with my ati video card........i tried a lot of things out from posts on forums regarding this problem, but none of it worked for me. So i reinstalled ubuntu hoping that i might be able to get it working if i start from scratch again..........but its just giving more issues now

right now my biggest problem is that i am not able to get any update packages

"sudo apt-get update" returns a long list of errors and fails in the form:
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty/multiverse Translation-en_CA           
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA      
  Could not resolve 'archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'fr.archive.ubuntu.com'
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) Could not resolve 'fr.archive.ubuntu.com'
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2](http://fr.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2) Could not resolve 'fr.archive.ubuntu.com'

your help is very much appreciated. 
thanks.
kuru

I am fairly sure that you have not done a complete re-install of Ubuntu as you think ...
automatix is **Not** recommended by Ubuntu developers/maintainers so the
getautomatix.com apt repo should not exist on a clean install ...

---

### Post by KuruJ on 2007-08-30
not a clean reinstall eh.......alright i was going with the flow of the live cd......i deleted the partitions i had the ubuntu boot and swap on (but kept the windows partition)......and repartioned and reinstalled....kind of assumed that would of been ok :S

guess i did get some junk leftover from the installation before..............so how is this gonna work now, can we fix this with the installation i have now........or do i have to format and reinstall again...........and if thats the case, is it possible to format a partition and not the whole hard drive??

thanks u all for your help

---

