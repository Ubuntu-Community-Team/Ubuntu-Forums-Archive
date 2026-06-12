---
title: "Mounting MacOS 7 Day Of The Tentacle CD"
date: 2007-09-13
forum: Apple PPC Users
---

### Post by lubosz on 2007-09-13
Hi, i'm trying to mount my 1994 [DOTT]("http://en.wikipedia.org/wiki/Day_of_the_Tentacle") for [mac os 7]("http://en.wikipedia.org/wiki/Image:Os761.png") game to run it in scummvm :D

Gnome says:
[IMG]http://www.omschallom.com/download/Screenshot-gnome-mount.png[/IMG]

Shell says:
```
bmonkey@burning-studio:~$ sudo mount -t [COLOR="DarkOrange"]hfsplus[/COLOR] /dev/cdrom1 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
```
bmonkey@burning-studio:~$ sudo mount -t [COLOR="DarkOrange"]hfs[/COLOR] /dev/cdrom1 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


dmesg says:
```
[ 1004.204000] hfs: unable to set blocksize to 1024
[ 1004.204000] hfs: can't find a HFS filesystem on dev sr0.
[11923.348000] hfs: unable to set blocksize to 1024
[11923.348000] hfs: can't find a HFS filesystem on dev sr0.
[12222.432000] hfs: unable to set blocksize to 1024
[12222.432000] hfs: can't find a HFS filesystem on dev sr0.
[12242.544000] hfs: unable to find HFS+ superblock
[12253.036000] hfs: unable to find HFS+ superblock
```

any ideas?

---

