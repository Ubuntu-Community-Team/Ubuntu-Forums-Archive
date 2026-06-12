---
title: "torrent downloading ports help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-12
For some reason, when I try to download some files they do not work but when downloading other files they do not work.  Why does it do this?  How can I check if my ports are open and how do I open them?  How do I configure the firewall?

---

### Post by hotweiss on 2007-11-12
Generally speaking you can't open any files until the torrent has finished. The reason for this is because Bit Torrent downloads random pieces of files rather than consecutive files. The firewall will automatically open ports for your bit torrent client. The easiest to use and most Bit Torrent client for Linux seems to be Deluge.

[http://deluge-torrent.org/News:Portal](http://deluge-torrent.org/News:Portal)

When installing Deluge the installer will guide you through with an easy to understand wizard.

---

### Post by inversekinetix on 2007-11-12
I highly recommend ktorrent. or uTorrent through wine (version 1,6,1 or earlier)

---

### Post by Dr Small on 2007-11-12
Deluge works good, for me.

---

### Post by hotweiss on 2007-11-12
> **inversekinetix said:**
> I highly recommend ktorrent. or uTorrent through wine (version 1,6,1 or earlier)

kTorrent if you use Kubuntu and Deluge if you use Ubuntu or Xubuntu, but yes kTorrent is an excellent app. The only advantage that Deluge has is ease of use.

---

### Post by damansandhu on 2007-11-12
you can use k torrent for downloading , it can be used in kde as well as gnome.

sudo apt-get install ktorrent


put you router in bridge mode and all your ports will be open.

code
sudo pppoeconf

---

