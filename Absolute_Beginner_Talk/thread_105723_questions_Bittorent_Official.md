---
title: "questions Bittorent Official"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2005-12-19
Bonjour! I have a simple question... is the deb package of the OFFICIAL BitTorrent compatible with Ubuntu Breezy? I heard that Debian's Deb is not always copatible with ubuntu's deb... [I'm assuming that the deb that Bittorent site provides is for Debian]

[http://www.bittorrent.com/](http://www.bittorrent.com/)

m... Well, i am just gonna try installing. And if I get a error... well, I know you guys are here with me ;)

---

### Post by ubuntu27 on 2005-12-19
Well I've trye installing Bittorrent... but had no luck...

```
ubuntu27@heaven:~$ sudo dpkg -i bittorrent-4.2.2.linux_i686-2_all_python2.4.deb
Password:
Selecting previously deselected package bittorrent-4.2.2.linux.
(Reading database ... 79566 files and directories currently installed.)
Unpacking bittorrent-4.2.2.linux (from bittorrent-4.2.2.linux_i686-2_all_python2 .4.deb) ...
dpkg: error processing bittorrent-4.2.2.linux_i686-2_all_python2.4.deb (--instal l):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/DownloaderFeed back.py', which is also in package bittorrent
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 bittorrent-4.2.2.linux_i686-2_all_python2.4.deb
ubuntu27@heaven:~$
```

---

### Post by bionnaki on 2005-12-19
just download the source
and run the bittorrent.py

no need to install anything.

---

### Post by claydoh on 2005-12-19
first try removing the bittorrent version you already have (the error you got leads me to believe you have it installed)

> sudo apt-get remove bittorrent
or use synaptic.

then you can install the deb from bittorrent.com using dpkg.  just choose a version marked "deb, python 2.4". It will not leave a menu icon iirc, but if you click a torrent link in firefox, you can use the "open with" dialog and browse to /usr/bin/ and select "bittorent" and ff should remember this if you check the "Do this automatically"  option.

---

### Post by ubuntu27 on 2005-12-19
[QUOTE=claydoh]first try removing the bittorrent version you already have (the error you got leads me to believe you have it installed)


or use synaptic.

then you can install the deb from bittorrent.com using dpkg.  just choose a version marked "deb, python 2.4". It will not leave a menu icon iirc, but if you click a torrent link in firefox, you can use the "open with" dialog and browse to /usr/bin/ and select "bittorent" and ff should remember this if you check the "Do this automatically"  option.[/QUOTE]
```

ubuntu27@heaven:~$ sudo apt-get remove bittorrent
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  bittorrent gnome-btdownload
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 766kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 79565 files and directories currently installed.)
Removing gnome-btdownload ...
Removing bittorrent ...
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
ubuntu27@heaven:~$ sudo dpkg -i bittorrent-4.2.2.linux_i686-2_all_python2.4.deb
(Reading database ...
79479 files and directories currently installed.)
Unpacking bittorrent-4.2.2.linux (from bittorrent-4.2.2.linux_i686-2_all_python2.4.deb) ...
Setting up bittorrent-4.2.2.linux (i686-2) ...
ubuntu27@heaven:~$ Password:
bash: Password:: command not found
ubuntu27@heaven:~$ sudo dpkg -i bittorrent-4.2.2.linux_i686-2_all_python2.4.deb
(Reading database ... 79689 files and directories currently installed.)
Preparing to replace bittorrent-4.2.2.linux i686-2 (using bittorrent-4.2.2.linux_i686-2_all_python2.4.deb) ...
Unpacking replacement bittorrent-4.2.2.linux ...
Setting up bittorrent-4.2.2.linux (i686-2) ...
ubuntu27@heaven:~$
```

Well, looks like it work...
Let me test byt downloading a torrent. 
And thank you claydoh for your help :)

---

