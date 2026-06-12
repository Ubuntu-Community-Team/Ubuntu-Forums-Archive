---
title: "VLC [region free trouble]"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Literatka on 2007-02-23
I cannot get my VLC to play region 0 dvds so I finally figure out what I need!

libdvdcss2 - and I can't get it. I've tried following these directions from VLC: 


Graphical way

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Note: to get libdvdcss (DVD region free software), you'll need to add the following repository to synaptic: deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free. (replace "edgy" with your ubuntu version name)

Search for vlc and install it. You should also install vlc-plugin-esd (and libdvdcss2).
Command line way

You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd

To install libdvdcss2 (DVD region free software) add "deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free" to your /etc/apt/sources.list file and run:

  % sudo apt-get install libdvdcss2


and this is what I get when I do it : (attatchment of screenshot)

and when I try to do it through terminal I get : 

jessica@jessica-laptop:~$  sudo apt-get install libdvdcss2
Password:************
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
jessica@jessica-laptop:~$

---

### Post by Muzik83 on 2007-02-23
Are you sure you "sudo apt-get update" ?

If you did, you can also do it manually by going here:
[http://www.debian-multimedia.org/pool/main/libd/libdvdcss/](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/)

and downloading the appropriate version of libdvdcss2, which is probably this one:
[http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb)

Double click the file to open with GDebi, the package installer and press the install button.

---

### Post by Literatka on 2007-02-23
Well I wasn't able to figure it out with VLC but Im using Xine now so it's working :D 

:popcorn: ( just because I wanted to use this one!)

---

