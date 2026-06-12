---
title: "Offline Installations"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Contemplator on 2007-04-23
When I first installed Kubuntu 6.10 Edgy, the first thing I wanted to do is listen to my music, which was saved on a NTFS HDD.. The permissions problem hit me.. The OS also could not shut down my PC automatically.. I decided to stop using until I get 7.04.

I installed 7.04, and it seems easier to use, except:

1. How do I get **OFFLINE** installations of stuff like NTFS-3G, Wine, Gnome, Fuse, ...
2. Give universal permissions to a partition (i.e., everyone can use the partition)?
3. Does 7.04, come with or need stuff like gksu, fuse
4. Is it Ubuntu legacy to never have offline executable installations (e.g., rpm's)

---

### Post by Cypher on 2007-04-23
I consider what you are asking a step backward in the evolution of Linux. The advent of APT/YUM and other services greatly ease the installation of new software by doing all depdency checking and getting them along with the intended software.

Before these services, if you wanted to  install Wine and it needed half a dozen other files, you didn't know that until you tried to install Wine, failed and then went searching for those other files.

In this age of ever-prevelant Internet access, it really makes no sense to force people to try to find all files themselves.

Would you expect Microsoft to stop using the Windows Update site and just publish randomly named files on some site, you have to admit that having that feature is of great ease to most users.

So unless you have a VERY good to reason to be offline, go online and get the apps you want.

Regards

---

### Post by hyperair on 2007-04-23
@Cypher
While it is a step backward it isn't right to deny him the ability of installing offline packages right? After all Linux is "free as in freedom", inclusive of Ubuntu. It should be flexible and whatnot.

@Contemplator
1. Go to Google and look for .deb files available for download. Then double click on them and install them
2. Simple: add everyone to the user group called "disk"
3. gksu comes with Ubuntu. 
4. I believe you meant "policy" as opposed to "legacy". Anyway, there are distribution-independent executable installers freely available online for certain packages, although you are advised to use the one in the repository. RPMs are NOT executable, please be reminded. RPMs are to Red Hat as DEBs are to Ubuntu. Install the "alien" utility to convert RPMs to DEBs for use in Ubuntu. While it is possible to install RPMs in Ubuntu by double clicking them, it is not advisable to do so.

---

### Post by Cypher on 2007-04-23
@Hyperair, rightly so I wasn't denying the OP the ability of getting the files, as you've outlined, you can search through a variety of sights inclued [http://packages.ubuntu.com](http://packages.ubuntu.com) and find all the .DEB files for download and install.

I was just suggesting that APT provides levels of service that greatly overcome whatever inconveneince there might be of going online to get a new application. 

Regards

---

### Post by Contemplator on 2007-04-24
Thanks for the help guys.

Offline:
- Coz the PC at home has no net (Net in Kenya is #$&*! expensive)
- I use the free net provided by my university to download (linux only - exe not allowed) 
  and use forums, email, ...

---

