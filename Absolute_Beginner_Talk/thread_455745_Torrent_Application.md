---
title: "Torrent Application????"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by TigerTail on 2007-05-26
Hello all Just joined this forum. After heavily debating on whether to keep windows or move onto Ubuntu. Well since I'm here you know what I picked. Well so far Ubuntu the only thing keeping me from switching over all my computers is the simple fact that I cant find a good torrent downloading software. I use bitlord on my windows based computer. Can anyone help me find and install one. Sorry I sound like a retard but hey I need to get answers somehow. thanx for everyones time.


LONG LIVE THE FREEWARE!!!!!!!!!!!

---

### Post by Frostmourne on 2007-05-26
Azureus (most full-featured) or Deluge (I haven't actually tried this but it looks good)

---

### Post by Nythain on 2007-05-26
the newest version of KTorrent, or wine your favorite windows client, i wine uTorrent at the moment

in my opinion, azureus is to much of a resource hog, and deluge just doesnt offer the options i need... KTorrent gets close, then again, you could just master the use of the official bittorrent client :)

---

### Post by TigerTail on 2007-05-26
Ok i Downloaded Deluge-0.5.0.tar.gz how do i go about installing it? Like i said newbie here. Im not an idiot when it comes to computers just trying to get used to linux. 

Thanx everyone :)

---

### Post by Nythain on 2007-05-26
extract the archive file somewhere then follow these directions... readme's are great
```

Deluge BitTorrent Client

Authors:
    Zach Tibbitts, aka zachtib
    Alon Zakai, aka kripkenstein

Homepage: http://deluge-torrent.org

==========================
Installation Instructions:
==========================

First, make sure you have the proper bulid
dependencies installed.  On a normal Debian
or Ubuntu system, those dependencies are:

python-all-dev
python-all
python-support
libboost-dev
libboost-thread-dev
libboost-date-time-dev
libboost-filesystem-dev
libboost-serialization-dev
libboost-program-options-dev
libboost-regex-dev
zlib1g-dev

But the names of the packages may vary
depending on your OS / distro.

Once you have the needed libraries installed,
build Deluge by running:

    python setup.py build

You shouldn't get any errors.  Then run, as 
root (or by using sudo): 

    python setup.py install

and Deluge will be installed.

You can then run Deluge by executing:

    deluge

```

---

### Post by fdrake on 2007-05-26
i like much better freeloader, its light and in same cases worked much better than Azureus in speed. to install open the terminal and type
sudo aptitude install azureus freeloader

to launch the program just go to the menu bar under internet you'll find both the programs

---

### Post by TigerTail on 2007-05-26
Thanx a million guys I'm surprised at how fast people respond here!!!
I ended up using this in the terminal

   sudo aptitude install subversion build-essential python-all-dev python-all \
     python-support libboost-dev libboost-thread-dev libboost-date-time-dev \
     libboost-filesystem-dev libboost-serialization-dev \
     libboost-program-options-dev libboost-regex-dev zlib1g-dev && \
     svn checkout [http://deluge-torrent.org/svn/trunk](http://deluge-torrent.org/svn/trunk) deluge && \
     cd deluge && python setup.py build && sudo python setup.py install

---

### Post by TigerTail on 2007-05-26
What tcp port should i use?

---

### Post by TigerTail on 2007-05-26
Ok nevermind I got it all figured out now!!

wow this may take a little more getting used to than I thought but all and all I think terminal is the greatest thing ever!

---

### Post by PGhacker on 2007-05-27
i recommend BitTyrant. A new Azureus based client developed by the Washington University. It supports Linux
[BitTyrant]("http://bittyrant.cs.washington.edu/"). The downloading speed is not very stable, but i always download a lot more than upload although i set to unlimited for down/upload. My ratio is ALWAYS below 0.2

---

### Post by Beatbreaker on 2007-05-27
> **Nythain said:**
> the newest version of KTorrent, or wine your favorite windows client, i wine uTorrent at the moment

I'm gunna work on getting uTorrent up and running also - it's the fastest, simplest and most effective client out there, i've recently gone from Azureus to uTorrent and haven't looked back

---

### Post by kbf on 2007-05-27
I use uTorrent 1.6.1 with wine and it works perfect and is fast and no memory hog. Have used a few other ones and would not go back:popcorn:

---

### Post by B00R4dL3y on 2007-05-27
I like uTorrent too, but I have a problem with it sometimes minimizing to the tray and now being able to restore the window.  Only way to restore the window is to delete all my settings, so uTorrent thinks it's starting fresh all over again.

---

