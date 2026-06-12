---
title: "Networking dual-boot and single boot macs"
date: 2005-05-01
forum: Apple PPC Users
---

### Post by G5LiMac on 2005-05-01
I'm having an networking problem, after a relatively painless install of ubuntu 5.04 on a dual 2Ghz G5 powermac dual-booting with OS X 10.3.9. The partitions were:
-Apple boot partition (32kb)
-Linux new world ppc boot partition (16Mb)
-Linux swap partition (2 Gb)
-Linux ReiserFS journalling root partition (45 Gb)
-Fat32 shared partition (/shared) (5 Gb)
-Mac HFS+ partition (100 Gb)

I also downloaded Kubuntu on the linux partition via apt-get. All systems work fine in 'stand alone' mode, and both KDE and GNOME desktops environments function.

However, when I try to network my G5 desktop with my laptop (G4 powerbook), both running OS X 10.3.9, I get a one-way failure. The G5 desktop can see and connect to the powerbook as usual. However, while the G4 powerbook can see the desktop via the 'connect to server' command, it fails to connect, claiming the the password is incorrect (and also states that the desktop cannot support SSH, which is also incorrect).

Has anyone had success networking dual-boot macs with other macs, both ways?
Any insights appreciated!!
Thanks
 ](*,)

---

### Post by Len on 2005-05-05
I have never had any problem with networking, and I have OS 9, OS X, Ubuntu and Gentoo installed on seperate partitions. It looks like an OS X problem, no idea on which side. AppleTalk was perfect on the old machines but with OS X it isn't always working flawlessly...

Redirecting you to [http://www.macfixitforums.com/](http://www.macfixitforums.com/)

---

