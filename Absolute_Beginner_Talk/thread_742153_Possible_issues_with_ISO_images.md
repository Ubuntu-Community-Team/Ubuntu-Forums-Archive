---
title: "Possible issues with ISO images"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by bxdobs on 2008-04-01
Ubuntu Newbee 

2 issues I have had with the ISO's tried so far

1) Ubuntu won't install  ubuntu-7.10-desktop-i386.iso 712,508 KB 
Issue: the partition process fails to find/configure a SWAP partition ... as this works fine with xbuntu 7.10, I expect there may be something wrong with the Ubuntu iso?

2) xbuntu 7.10 desktop 579,970 KB installed ok but appears to be missing Alien for converting rpm packages is this by design?
Issue: apt-get install alien keeps coming back and saying it can't find alien so fails to install ... can't find alien on the CD or the HD  ... it also  appears to be missing from the list files in /etc/apt/  
Reading through some of the threads there seems to be some confution on what should be available in the various versions of ubuntu

---

### Post by ugm6hr on 2008-04-01
Is Xubuntu connected online?

Have you enabled all the repos?

Alien is not installed by default.

---

### Post by smurphy_it on 2008-04-01
I've never had any problems with the desktop CD.  Did you do a MD5 checksum check to verify the .ISO had the right MD5 Checksum before burning it ?

Did you choose, Check CD for defects after burning and booting the CD ?

Alien... No idea.  Never had to use it.  Understand the premise of it, but never had a need to convert a .rpm over to a .deb

---

### Post by philinux on 2008-04-01
> **bxdobs said:**
> Ubuntu Newbee 

2 issues I have had with the ISO's tried so far

1) Ubuntu won't install  ubuntu-7.10-desktop-i386.iso 712,508 KB 
Issue: the partition process fails to find/configure a SWAP partition ... as this works fine with xbuntu 7.10, I expect there may be something wrong with the Ubuntu iso?

2) xbuntu 7.10 desktop 579,970 KB installed ok but appears to be missing Alien for converting rpm packages is this by design?
Issue: apt-get install alien keeps coming back and saying it can't find alien so fails to install ... can't find alien on the CD or the HD  ... it also  appears to be missing from the list files in /etc/apt/  
Reading through some of the threads there seems to be some confution on what should be available in the various versions of ubuntu

1. Make sure you burn at 4x.  Select the option to check the disk for errors.

2. Alien is not installed by default. Check your sources lists are enable correctly to install via synaptic.

---

### Post by caravel on 2008-04-01
> **philinux said:**
> 1. Make sure you burn at 4x.  Select the option to check the disk for errors.

I see this advice a lot and often repeat it myself.  My question is that why burn at 4x?  I have burned discs many times and never had a problem at higher speeds, so why does the Ubuntu ISO have issues that cause so many on here to recommend burning at slower speeds?  Is this just a failsafe method in case the user has a dodgy rewriter?

Thanks

Caravel

:)

---

### Post by philinux on 2008-04-01
> **caravel said:**
> I see this advice a lot and often repeat it myself.  My question is that why burn at 4x?  I have burned discs many times and never had a problem at higher speeds, so why does the Ubuntu ISO have issues that cause so many on here to recommend burning at slower speeds?  Is this just a failsafe method in case the user has a dodgy rewriter?

Thanks

Caravel
:)

Although the live cd iso is only 690 meg. It contains gigabytes of compressed data. The faster the burn the more chance of minor errors creeping in. Hence the md5sum check and check cd for defects.

---

### Post by bxdobs on 2008-04-01
Thanx for the quick responses

Xbuntu is online

As stated alien appears to be missing from the list files

not sure how to test a checksum ... still have the downloads so please provide some more info

All iso's were created and verified with Nero at 4x

How does one Enable all repos

---

### Post by philinux on 2008-04-01
To check the cd boot up the live cd. When the menu appears one of the options is 

check cd for defects

---

### Post by ugm6hr on 2008-04-01
This will help you change repo sources: [http://ubuntuforums.org/showpost.php?p=4030951&postcount=16](http://ubuntuforums.org/showpost.php?p=4030951&postcount=16)

---

