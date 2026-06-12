---
title: "Troubles with Updating Firefox and various other newbe issues..."
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by mark2 on 2005-09-02
Firefox says... Fatal Error [-618]: Couldn't open xpistub library.

That and I was wondering if someone could tell me how to get gnome how to mount NTFS drives?

Also, i cant do the sudo apt-get thingy to install KDE... it says its missing or something random like that.

Specs:

P4 1.7Ghz
512MB Ram
(for ubuntu) 2.5Gb hdd (yea i know its tiny)
40GB hdd for XP
SiS 650 Chipset/Video (YEA i know... stupid crappy intergrated video)

---

### Post by KingBahamut on 2005-09-02
For kde 

apt-get install kubuntu-desktop 

Mounting NTFS drives 
add the below line to fstab in /etc 

where hd1 equals the parition your mounting
and /media/windows is your mount point.  
/dev/hdx1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

