---
title: "Which Torrent downloader to use?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by grs on 2007-02-08
I'm looking for something like Bit Torrent to download torrent files through Xubuntu, I just mentioned Bit Torrent because thats what I use on my Win XP laptop. Any suggestions/versions?

---

### Post by xpod on 2007-02-08
Azureus is what i now use and it`s been great..

---

### Post by tbroderick on 2007-02-08
rtorrent

---

### Post by yhotg on 2007-02-08
hi

i don't know xubuntu, maybe it has a torrent downloder of it own.
I use Ktorrent, 
sometimes, Bittornado. It's for the console.

---

### Post by Frak on 2007-02-08
µTorrent, works natively under WINE like it was working within Windows, and its the lightest Torrent.

---

### Post by NicePics13 on 2007-02-08
Azureus is one of the best free bittorrent clients out there, but a memory hog and even unusable if you have very little RAM installed.

---

### Post by geokok1981 on 2007-02-08
BitTornado does it for me.

---

### Post by ADT on 2007-02-08
bittornado-gui is a very good torrent client and it's light on the system too.

```
sudo aptitude install bittornado-gui
```

---

### Post by AndyCooll on 2007-02-08
KTorrent is good too. I prefer GNOME apps usually, however this is one KDE app I still like to install.

:cool:

---

### Post by grs on 2007-02-08
I was just looking at µTorrent, what is WINE? is it a version of Linux, will µTorrent work with Xubuntu?

---

### Post by Nakkis on 2007-02-08
I'd suggest you rtorrent if you aren't afraid of console programs. It's super easy to manage my torrents remotely with rtorrent + screen and a ssh session.

---

### Post by dr_d on 2007-02-08
Okay here's my experience:


the default bittorrent program that comes with ubuntu can only run a single torrent at a time - a huge restriction. it also does not have much functionality as far as selecting which files from within a torrent to download etc etc.

bittornado or bittornado -gui or whatever it's called can handle multiple torrents at a time... however it requires you to manage them each in a separate instance of the program -- which i do not approve of. it has much greater functionality than the previously mentioned client but i find the  GUI messy and hard to use.

The Azureus from the repos is a mess.. it works but barely. Unless it's changed since I last tried it you will have to play around with it for ages to get anything out of it. It runs off of java which is a big turn off for me as it makes it slow. Apparently you can get a newer version if you compile the source yourself but then the program cannot be updated via synaptic.

uTorrent works fine under WINE however it is closed source. Otherwise a great client.

KTorrent -- never tried it... considering it's for KDE i probably never will either :)

rTorrent - a truly great command line client. It has all the functionality you could ever want and at the same time it's easy to use (once you learn the key shortcuts) and very very light on the system. You can also run it inside a screen session so you can ssh into you computer and re-attach the screen session and check how the downloads are going.


I hope that helps you out a bit.
Cheers.

---

### Post by NicePics13 on 2007-02-08
WINE is a windows compatibility layer for Linux, enabling you to run (some) windows programs. Such as µTorrent.

---

### Post by garybrlow on 2007-02-08
If you're used to uTorrent, it runs via WINE and doesn't require Java. It is more system resource friendly compared to Azureus even on windows. Azureus is currently the best client in terms of features but since it uses Java it tends to be a resource hog and is not for older pcs or pcs with 256MB of memory below, uTorrent comes second interns of features. There is Azureus 3/Zuedo which seems to be more resource friendly on windows, haven't tried yet on Linux. For native lightweight applications there is Ktorrent and Deluge but still lack functionality and customizability compared to uTorrent and Azureus. There is actually talk of plans for a Linux version of uTorrent but time only knows when that will happen. :p

Cheers!!!

GaryBrlow :D

---

### Post by dorcssa on 2007-02-08
I use µtorrent too, and I think it's great, at least it's working fine for me.

---

### Post by grs on 2007-02-08
Dr_d

Thanks for that guide, I'm still not to sure on all the terminology but you've giving me something to work from.

---

### Post by anaconda on 2007-02-08
I use Ktorrent.. beacuse it is easy to install and get going (from the repositories) and it is a LOT like azureus, but lighter

---

### Post by bogolisk on 2007-02-08
Transmission is very simple and good. It has gnome/gtk and console modes. It supports uPNP so it can request your uPNP-aware router to open its port automatically.

[http://gnomefiles.org/app.php/Transmission](http://gnomefiles.org/app.php/Transmission)

Its limitations: no support to pick-n-choose files inside a torrent (all or nothing), no detailed view of your peers and their stats, no support for kick-n-ban.

It's a very nice BT client for beginners. I'm no BT nub, but I still like transmission for its simplicity.

---

### Post by clu on 2007-02-08
If you even plan on using private trackers you would be better off sticking with Azureus, uTorrent with WINE, or rtorrent.     These three are approved on most private trackers and most other programs are not.         

I use uTorrent currently but would use Deluge if it wasn't banned on some trackers.

---

### Post by stoeptegel on 2007-02-08
> **clu said:**
> 
I use uTorrent currently but would use Deluge if it wasn't banned on some trackers.

That is true in some degree, but please let me add to that before people will jump into conclusions, that deluge is not banned because of an error in de client code.
Afaik it was banned on some higher-end trackers because of the fact that they didn't liked the used engine libtorrent that much. Also, most trackers do only want to support the bigger clients because that is hard enough to manage as it is (depending on the quality they want to deliver), while still supporting the freedom of choice to it's users. (so that makes blacklisting rather easy)

 But it looks to me that the latest version of libtorrent is considered to be 'well enough' by now, for what that counts. So that is good news. :)

---

### Post by xlinuks on 2007-02-08
I have always used Azureus on Linux (and uTorrent on Windows in the times when I was a windows user), and it's everything I ever needed, there's nothing I can complain about. You might consider installing Java 6 since it has the fastest GUI in comparison with previous Java versions - that would make Azureus GUI faster.
Can't say whether it consumes much RAM cause I have 1.5GB of ram and the memory has never been an issue for me, also, from the config file for Azureus 2.5.0.4 it says that it uses min 16MB and max 128MB, which I find normal for a program that is supposed to download lots of files at once.
..just my plain 2 coins

---

### Post by hoagie on 2007-02-20
I use ktorrent and azureus. Ktorrent right is flying while azureus is stuck at 0. Although it might be the torrent health since the one that I download from ktorretn has 100 peers while azureus only 7.

---

