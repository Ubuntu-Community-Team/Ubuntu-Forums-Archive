---
title: "burning livecd on OS X 10.4 truncates file names"
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by cfr42 on 2011-04-15
I've been having problems creating a LiveCD for Ubuntu. I started using the iso for 10.10 but it seems that is likely buggy so I've switched to that for 10.04. (History is at[]("http://ubuntuforums.org/showthread.php?p=10679530#post10679530") [http://ubuntuforums.org/showthread.php?p=10679530#post10679530](http://ubuntuforums.org/showthread.php?p=10679530#post10679530).)

I'm posting here because I think the problem I'm now having must be either a problem with my burner or a problem with the software I'm using and, either way, Apple-specific.

System: PPC 1.5 GHz 1.25GB RAM nVIDIA GeForce FX Go5200 64MB VRAM SuperDrive
OS: Mac OS X 10.4.11

I've been mostly following the standard Disk Utility instructions - open DU, drag image to left side pane, click to burn, insert media (tried DVDs, CDs) and set to lowest speed, verify and eject when done. Burns fine. Burn is verified.

Download SHA256 sums match those published, files of sums checked using gpg.

The problem is that the md5sums for the files which should be on disk don't check out because long file names are being truncated. So lots of the .deb files are not .debs at all because the version which ends up on the disk has a name which doesn't contain all the characters.

Does anybody have any suggestions for burning an .iso image under 10.4 in such a way that long file names are preserved? (I'm assuming this is the problem though I can't tell what's on the .iso image since I'm not mounting it - indeed, OS X refused to mount the 10.10 image when I tried this.)

Any suggestions would be much appreciated.

---

### Post by cfr42 on 2011-04-16
Posted in wrong thread

---

