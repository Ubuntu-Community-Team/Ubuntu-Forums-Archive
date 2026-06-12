---
title: "playing MP3 / AVI over network does not work"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by gjmoyer on 2006-11-12
I love Ubuntu, very impressed with what it offers.  After struggling for a week to get wifi working on Fedora FC6, I loaded Ubuntu and it worked right away without me doing anything!  Thank you!!

I have mplayer installed, and I would like to play an AVI file that is on my Windows XP machine shared drive.  I did a connect to server, and see all the files on my Windows XP share.  When I click one of my AVI files, it pops up the Totem Movie player but then says "Could not read from resource.".  I also tried the same with Mplayer, and with loading MP3's.

My question is, what is the trick for playing these files over a network connection through a windows share?

---

### Post by tim15856 on 2006-11-12
I haven't been able to directly load any file from my file server into a program running in Ubuntu. I always have to copy the file to the local drive home folder. I'd also like to know if it can be done.

---

### Post by gjmoyer on 2006-11-15
I found that if you mount the share, then it works without issue as if it is a local drive.  After mounting it looks like a folder on the machine.  I had thought after using the "network server" GUI, that it would work that way.  You can setup the system so that the mount happens automatically each time you login.  Do a search on Samba mount windows shares.

---

### Post by jms1989 on 2006-11-15
I would like to do this with Apache2 hosting a file from this computer to my home network. btw, I run Ubuntu and the Client is WinXP.

---

### Post by tim15856 on 2006-11-15
> **gjmoyer said:**
> I found that if you mount the share, then it works without issue as if it is a local drive.  After mounting it looks like a folder on the machine.  I had thought after using the "network server" GUI, that it would work that way.  You can setup the system so that the mount happens automatically each time you login.  Do a search on Samba mount windows shares.

The remote share is mapped to my desktop. I still can't directly run the data files.

---

### Post by eighthate on 2006-11-15
have you tried installing the codecs from synaptic?

---

### Post by tim15856 on 2006-11-17
The codecs aren't the problem. The files play fine when they are on the local disk. Our problem is trying to play them from a remote network share. It's not just mp3 files either. If I try to double click on a jpg or other type of data file, they won't load up into the proper program. They all work fine when I copy them to the local disk.

---

### Post by nexu56 on 2006-11-18
I experienced the same problem after upgrading to edgy. The problem seems to be related to the latest version of Gnome, specifically gnome VFS. [Here is one of many bugs filed.]("http://bugzilla.gnome.org/show_bug.cgi?id=359133") One way to get around this would be to connect to your windows share by installing smbfs and mounting the windows share via fstab.

---

