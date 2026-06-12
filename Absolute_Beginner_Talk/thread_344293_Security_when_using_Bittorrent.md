---
title: "Security when using Bittorrent"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by tyler_roach on 2007-01-22
Hi,
Are there any particular security measures I should take when using Bittorrent clients to keep my computer from being compromised?

---

### Post by carverj on 2007-01-22
Apparantly there is a vulnerabilty scanner available named Nessus. Perhaps you could give that a try. Also are you behind a firewall? You may need to utilize port forwarding if you are using a router!

---

### Post by userundefine on 2007-01-22
Apart from certain Windows clients full of junk or spyware, there is nothing inherently compromising about BT, anymore than using FTP or HTTP.

---

### Post by ardchoille42 on 2007-01-22
> **userundefine said:**
> Apart from certain Windows clients full of junk or spyware, there is nothing inherently compromising about BT, anymore than using FTP or HTTP.

That is good to know. I have always avoided BT because I don't totally understand how it works.

---

### Post by Shatrat on 2007-01-22
As long as you trust whoever uploaded the original file and hosts the torrent tracker, you can trust the file you recieve at the end.  

If by security you mean hiding your IP from the mafIAA when downloading copyrighted works, there is no protection built into bit torrent for that.  There is a plugin for Azureus called Safepeer which blacklists connections from IP addresses and ranges known to belong to the riaa and mpaa and people working for them.  It isnt foolproof though, it is easy for someone to get a new IP.

---

### Post by userundefine on 2007-01-22
> **ardchoille42 said:**
> That is good to know. I have always avoided BT because I don't totally understand how it works.
It's very simple actually, and very efficient.

I have a file that I want to share people.  Let's say it's the source code for the latest version of Apache.  So, there are a lot of people who are going to want it.  I have a webserver, but I've got bandwidth limitations and I can't afford to upgrade.  So, what I do is I use BitTorrent to distribute it.  I use my webserver to set up a BitTorrent tracker so there's a single point where people can get the .torrent file, which is essentially a small container of metadata about the specific file I want to share.  The tracker tracks the number of people who start downloading the torrent file, because a BT client announces itself to the tracker to get a list of peers.  So, I become the uploader of the file through BitTorrent to 500 users, and then once I get a full copy out there then there are two people from whom you can get the file.  With 500 people on a torrent, there become 500 people (eventually) with the file, and then the combined speed of those 500 people uploading becomes the speed of the torrent.

So, you see, it's very efficient and great for servers since my hypothetical webserver isn't using really any bandwidth at all: it's all the peers seeding and leeching the file giving their bandwidth.  The server stays up, I have no outrageous bandwidth bills, and the file is spread around efficiently and there is no single point of failure (i.e., only one source) of the file now.  And, if for some reason my .torrent file is no longer accessible, anyone can make a .torrent again and upload it to any BT tracker, and, as long as they don't modify the file (meaning it has the same hash as when I originally uploaded it), everyone who previously downloaded it can help seed it again.

---

