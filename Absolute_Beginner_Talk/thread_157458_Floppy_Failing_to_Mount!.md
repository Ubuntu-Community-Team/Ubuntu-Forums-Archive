---
title: "Floppy Failing to Mount!"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by yotman on 2006-04-09
Just installed Ubuntu 5.10 on our computer but it cannot recognise the Floppy Drive. "Unable to mount the selected volume" is displayed whenever I try to open the drive.

How do I get round this problem?

---

### Post by Kapre on 2006-04-09
[QUOTE=yotman]Just installed Ubuntu 5.10 on our computer but it cannot recognise the Floppy Drive. "Unable to mount the selected volume" is displayed whenever I try to open the drive.

How do I get round this problem?[/QUOTE]

It was a bug. Fixed already. try using [this ]("http://doc.gwos.org/index.php/Floppy_mount_issues")

---

### Post by yotman on 2006-04-09
[QUOTE=Kapre]It was a bug. Fixed already. try using [this ]("http://doc.gwos.org/index.php/Floppy_mount_issues")[/QUOTE]

I followed the intructions. It looks like the computer has to be connected to the internet, because it kept mentioning that certain files were not fetched. The computer that has the Linux is not connected to the internet. At the moment I can not get it connected. What do I do?

---

### Post by StefanoCole on 2006-04-10
From a terminal window type the following:

sudo mount -t vfat /dev/fd0 /media/floppy0

when you have finished with the floppy unmount it before ejecting:

sudo umount /media/floppy0

Stefano

---

### Post by yotman on 2006-04-13
[QUOTE=Kapre]It was a bug. Fixed already. try using [this ]("http://doc.gwos.org/index.php/Floppy_mount_issues")[/QUOTE]

I managed to get the computer online and followed the instructions as listed above. And this is what I got. 

What do I do next. I am lost.

<hr>

root@ubuntu:/home/mvula# apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 2B in 8s (0B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release)  Unable to find expected entry  deb/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/deb Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_deb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/http://ubuntu-backports.mirrormax.net/ Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_http:__ubuntu-backports.mirrormax.net__binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/breezy-extras Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/home/mvula# apt-get install pmount
Reading package lists... Done
Building dependency tree... Done
pmount is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/deb Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_deb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/http://ubuntu-backports.mirrormax.net/ Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_http:__ubuntu-backports.mirrormax.net__binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/breezy-extras Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
root@ubuntu:/home/mvula#

---

### Post by Sef on 2006-04-13
You need to Add multiverse and universe:

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

