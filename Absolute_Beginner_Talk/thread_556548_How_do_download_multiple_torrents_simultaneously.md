---
title: "How do download multiple torrents simultaneously?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by northerndude81 on 2007-09-21
It's great that BitTorrent is built into Ubuntu but why won't it let me download more than one torrent simultaneously?  If I have one torrent downloading and try to start another it gives me an error.  (Is this normal or just something wrong with my setup?)

What is the best way for me to download more than one torrent simultaneously?  (I tried Azureus but was not savvy enough to figure out the proper settings and so downloads were intolerably slow... I need a SIMPLE, easily understandable solution.)  Thanks.

---

### Post by julian67 on 2007-09-21
Probably the nicest BitTorrent client for Gnome now is [Deluge](http://deluge-torrent.org/)

You can get a deb for feisty [here](  http://deluge-torrent.org/downloads)

You'll be able to download and upload multiple torrents simultaneously, and it's a nice looking easy to use client.

---

### Post by northerndude81 on 2007-09-21
Will it function properly upon the install, or will it require that I change or input a bunch of numbers and codes that I'm not going to know or understand (like Azureus did)?

---

### Post by PmDematagoda on 2007-09-21
If codes and numbers meaning a little bit for configuring your connections then most probably you will have to, but it is easy to understand and is just a simple formality, if it is there of course. I don't use Deluge, I use Azureus, really customisable and useful in my opinion.:)

---

### Post by stmiller on 2007-09-21
Or try [ktorrent]("http://ktorrent.org/").
```

sudo apt-get install ktorrent

```

---

### Post by julian67 on 2007-09-21
> **northerndude81 said:**
> Will it function properly upon the install, or will it require that I change or input a bunch of numbers and codes that I'm not going to know or understand (like Azureus did)?

Don't worry, it's much easier and simpler than Azureus. Probably the default settings will be OK for you.

---

### Post by lespaul_rentals on 2007-09-21
> **stmiller said:**
> Or try [ktorrent]("http://ktorrent.org/").
```

sudo apt-get install ktorrent

```

I agree.

I don't know if you mind changing or if you are determined to stick with BitTorrent and fix it.  If the latter is the case, ignore me.  But I really feel that Ktorrent is one of the greatest BitTorrent clients ever, regardless of platform.  I was downloading at 160-170 KB/s when my internet connection is capped at 150 KB/s

---

### Post by julian67 on 2007-09-22
I would use Ktorrent if you use Kubuntu and Deluge if you use regular Ubuntu or Xubuntu. They are both excellent clients with very similar abilities. Deluge has improved dramatically in the last few months and there's not really anything to choose between them.

---

### Post by diskotek on 2007-09-23
i was using ktorrent which was great. but now i2ll give a try to deluge... i hope it would be satisfying as ktorrent.

---

### Post by msghaleb on 2008-03-24
Hi I downloaded Deluge and using it, but how can I configure it to download everything in the same time without queuing? I mean like the usual torrent clients.

Thank you

---

### Post by msghaleb on 2008-03-24
Got it in the Help menu -> configuration wizard -> Max Active Torrents.

Cheers and sorry for the stupidity :)

---

### Post by sloggerkhan on 2008-03-24
If you want something simple that does multiple downloads at once, try transmission. Others sounds like they'll be too complicated for your needs. It's in the repos.

---

### Post by Darganot on 2008-03-24
You can set how many download and upload slots you want in the options or preferences.  It's usually based on your connection speed, so make sure that's set correctly.  

Also if you want proper throttling you should cap your upload speed at least.  Check out a document called "The Bittorent Bible" found on many p2p sites for more information.

---

### Post by notwen on 2008-03-24
I'd recommend KTorrent or Deluge, depending on your preference.  Both are great torrent apps.  =]

---

