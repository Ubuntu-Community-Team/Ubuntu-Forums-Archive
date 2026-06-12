---
title: "torrent help"
date: 2007-02-13
forum: Apple PPC Users
---

### Post by maniacrobbins on 2007-02-13
i'm trying to find a good torrent downloading program to work with Ubuntu and my PPC processor.  BitTorrent doesn't work.  Everytime I try a torrent with it some message pops up and it doesn't download.  KTorrent speeds are so slow (1-5 kbs) it's not worth using.  Can anybody suggest a good program?

Thanx
Dave

---

### Post by seebol on 2007-02-13
I use deluge-torrent . One bug with it is that if you are using firefox and select the "Open this file with..." option instead of "Save to disk" for the .torrent files, deluge will open, but it won't be running anything. You then have to click on the "Add torrent" button to get started.

---

### Post by renzokuken on 2007-02-13
i personally lurv bittornado...... [www.bittornado.com](www.bittornado.com) 

theres also azureus (which i dont like)

both can be installed easily using automatix [www.getautomatix.com](www.getautomatix.com)

also rtorrent, deluge .......

---

### Post by maniacrobbins on 2007-02-14
Alright.  I'm trying to install Deluge but this is the second day I have ever used Ubuntu.  I switched from OSX and I'm not sure on how to install programs.  Any help with installing libtorrent-python and Deluge?

thanx
Dave

---

### Post by renzokuken on 2007-02-14
have you tried

```
sudo apt-get install deluge
```

dependencies should be taken care of for you this way

---

### Post by grazie on 2007-02-14
Deluge hasn't made it into the repos yet. I think it's going to be a great client, but a fair amount of work is still needed. You can get the .deb package from [here]("http://packages.debian.org/cgi-bin/download.pl?arch=powerpc&file=pool%2Fmain%2Fd%2Fdeluge-torrent%2Fdeluge-torrent_0.4.1-2_powerpc.deb&md5sum=45c7e60324261f563cdac15af6e6d0b2&arch=powerpc&type=main"). I suppose the most popular linux gui clients are BitTornado (which has limitations) and Azureus (which gobbles your resources). KTorrent is supposed to be good if you're using KDE. Maybe your slow speed is for other reasons.

---

### Post by maniacrobbins on 2007-02-14
> **renzokuken said:**
> have you tried

```
sudo apt-get install deluge
```

dependencies should be taken care of for you this way

This didn't work.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge

Thats what happened when I put it into the terminal.  Any suggestions?  
P.S.  Don't I have to do something with python-libtorrent first?

---

