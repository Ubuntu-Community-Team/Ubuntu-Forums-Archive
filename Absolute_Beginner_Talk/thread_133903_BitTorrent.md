---
title: "BitTorrent"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by FinePix on 2006-02-21
Im Very new to Ubuntu. Im using Ubuntu 5.10. Under Application Internet, theres BitToorrent. When i clik this button it says "Open location for BitTorrent meta fil".

Can some one explain what is this? and help me how to use BitTorrent.

---

### Post by MadL on 2006-02-21
Usually, you will have to go to a website that hosts a BitTorrent file (often just referred to as a "torrent"). When you select the link for the torrent, BitTorrent will open up and start downloading (and uploading) the file.

There's a pretty good FAQ on BitTorrent at [http://dessent.net/btfaq/]("http://dessent.net/btfaq/"). As it notes, the FAQ is written by a Windows user, but most of the principles should be the same for Linux.

**Edit:** Just to show you what a couple of webpages with links to torrents look like: if you look on the [download page for Ubuntu]("http://www.ubuntu.com/download"), you'll see a link for "BitTorrent" that will take you to a page of torrent links. And [here's]("http://www.us.debian.org/CD/torrent-cd/") the page for torrents on debian.org's website.

---

### Post by Ozitraveller on 2006-02-21
[QUOTE=FinePix]Im Very new to Ubuntu. Im using Ubuntu 5.10. Under Application Internet, theres BitToorrent. When i clik this button it says "Open location for BitTorrent meta fil".

Can some one explain what is this? and help me how to use BitTorrent.[/QUOTE]


You would download a torrent file to you harddisk somewhere, e.g. from a page like:

[http://cdimage.ubuntu.com/releases/dapper/flight-4/](http://cdimage.ubuntu.com/releases/dapper/flight-4/).

Find the link to: dapper-install-i386.iso.torrent

it's a small file so it won't take long to download. It contains the information about what to download. The torrent file above is the torrent for the iso image for dapper flight-4.

Hope that helps.

---

### Post by Madpilot on 2006-02-21
The "BitTorrent meta file" that GnomeTorrent is asking for is this little .torrent file, btw.

It tells GnomeTorrent where to go to get the actual file, and stuff like that.

BitTorrent is great - I get a lot of (legal) concert recordings from [http://bt.etree.org](http://bt.etree.org) with it.

---

### Post by Resurrection on 2006-02-21
To add to the discussion:  

I haven't used BT on Linux yet, but I have used it for several years now on Windows.  Basically what Bittorrent is is a Peer to Peer Network protocol.  Every file (or group of files) that you want to download on a Bittorrent network have to have a .torrent file.  Using a program designed to handle .torrent files, you can download just about anything.  

BT has many many legitimate uses, but by far the number of people using it for illegal (depending on where you live) purposes outnumber those legal users by hudreds of thousands of times.  BT allows you to download very large files, like the ubuntu .iso much faster than you could normally.

How it works is a .torrent file contains info about the file(s) you are going to download and info about what its "tracker" is.  A tracker keeps track of how many people are uploading (usually called seeding), downloading (leeching), the particular torrent that you want.  Your BT program will use the .torrent file (usually a small file) to connect to the tracker.  After gather some information, you will begin to download pieces of your file(s).  You will also upload back as well.  Simply put, the more people who are seeding a particular torrent the better your speeds will be.  You get the best speeds when the ratio of seeders / leechers is very high.  

As an example, I tried to download the ubuntu install .iso off the downloads page and I watched it download at around 25 kB/s.  Pretty slow.  I found a torrent for the same .iso on a BT indexing site (not going to list the site here as it has illegal content, and not sure about how that goes over here) and I was able to download the .iso at more than 450 kB/s.  So it didn't take me very long to get my .iso.

Also, the unwritten rule is that you should always share back a file you download at least once over.  In other words, you download a file that is 100 mB, you should upload at least 100mB back before stopping the BT program.

Personally I like Bittornado (Also know as the Shadow's Client) for Windows use, and I plan on trying it on Ubuntu.  Supposedly it should work since it is Python based.  Get it here:
[http://www.bittornado.com/download.html]("http://www.bittornado.com/download.html")

---

### Post by MadL on 2006-02-21
Good point -- just as there's more than one program you can use to, say, download by FTP or to unzip a file, there's more than one program you can use to download a torrent. They all use the BitTorrent program as their base, but they add different features that give you more control over loading the torrent. After you've tried using BitTorrent a few times, you may want to use one of these other programs.

I agree that Bittornado is a solid choice; you can also get it using the Synaptic Package Manager. Personally, I've been using Azureus as of late (only on Windows so far; haven't downloaded a torrent using Ubuntu yet) -- you can use Automatix to install it in Ubuntu. Azureus does have a reputation as a resource hog, but it worked fine on my old 128MB RAM Win2k box.

Hope this helps.

---

