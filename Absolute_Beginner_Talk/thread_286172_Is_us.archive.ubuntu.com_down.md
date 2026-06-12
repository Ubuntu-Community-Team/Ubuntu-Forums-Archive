---
title: "Is us.archive.ubuntu.com down?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-27
I have installed Edgy from a ISO CD that I downloaded and I am impressed with Edgy after trying to get Dapper to work the way I wanted.

I had a few problems getting my Canon LiDE 60 scanner working with Breezy 5.10.  With Edgy I just installed SANE and walla my scanner started working great. 

The speed of Edgy is very fast on boot and on shutdown. The wifi pcmcia card ( Dlink DWL-G630 ) worked out of the box.

My current problem is the Ubuntu download servers down?

Yesterday I was able to use Synaptic to install programs but today the link to ubuntu times out.

Any ideas on if the servers are down

---

### Post by PriceChild on 2006-10-27
which mirror are you using?

---

### Post by kent41 on 2006-10-27
> **PriceChild said:**
> which mirror are you using?

Synaptic times out and I get this
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.6-3ubuntu3_i386.deb
```

---

### Post by PriceChild on 2006-10-27
Yeah i've seen a lot of people saying that us.archive is down.

You could try a different server or maybe be patient?

---

### Post by kent41 on 2006-10-27
> **PriceChild said:**
> Yeah i've seen a lot of people saying that us.archive is down.

You could try a different server or maybe be patient?

Ok I can wait if other people are having the same problem 

Thanks for the reply

---

### Post by PriceChild on 2006-10-27
i've changed the name to help you get a response :)

---

### Post by Brunellus on 2006-10-27
The servers are getting HAMMERED.  If there is no compelling reason to upgrade from dapper... please consider waiting a few days, or maybe a week for the load to ease up.

---

### Post by mcpish on 2006-10-27
For the next release, Ubuntu should look at slightly modifying the apt system repositories so that they'd be "bittorrent" repositories.  Imagine if instead of pointing to an http address, the /etc/apt/sources.list file would point to varoius torrent trackers and the updates would come in via bittorrent protocol.  That way, when a new version comes out, the more people updating, the better the performance for the repositories.

---

### Post by kent41 on 2006-10-28
Are there other sites besides  us.archive.ubuntu.com that I could download applications with Synaptic Manager?

---

