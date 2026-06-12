---
title: "noob trying with azureus"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by mamboze on 2008-04-14
Hi,
I've installed and configured azureus OK (I think). But what do I do from now on. I've checked out the azureus help, but I'm still not clear with the actual download procedure. LIke, what exactly does the .torrent file do? and what is a torrent tracker? also, just one more question not on topic, azureus has installed a .azureus folder on the hard drive but I can't find it using nautilus, is this a hidden file?

thanks in anticipation

---

### Post by PmDematagoda on 2008-04-14
About the hidden folder, yes it is indeed hidden since it's name is appended with a ".", you append a "." to a file/folder name in order to hide it.

---

### Post by hyper_ch on 2008-04-14
[http://en.wikipedia.org/wiki/BitTorrent_(protocol](http://en.wikipedia.org/wiki/BitTorrent_(protocol))

---

### Post by scorp123 on 2008-04-14
> **mamboze said:**
>  I'm still not clear with the actual download procedure. LIke, what exactly does the .torrent file do? and what is a torrent tracker? A torrent file is like a map or a city guide ... It tells your program where on this planet all the the bits and bytes of the stuff you want to download are located. "Chunk #1 is on this computer in France here, Chunk #2 is on this Swiss computer over there, Chunk #3 is available from several computers in the USA - cool, we can download them in parallel - ... Chunk #233345553 is available from this Swedish computer over there ... ". That's how BitTorrent works. All the files you download are divided into tiny little chunks. So instead of having to download one large file from one single source (as in HTTP or FTP transfers) you could download many thousand tiny chunks from multiple sources (called "seeders" in BitTorrent lingo) at once.

A "tracker" is a web site that keeps track of who's got what. It's like a traffic information center that in addition to your torrent file (e.g. road map to where all the chunks are) keeps track of updates, traffic flows (e.g. which host can up- and download at what speed?) and announces these changes and upates to your program (e.g. Azureus).

Word of advice: Once a download is finished you are expected to **"keep seeding"**, e.g. help distributing whatever you downloaded (e.g. a DVD ISO of a Linux distribution?) by uploading to others and thus by letting others download the stuff from you. This usually happens automatically. So please don't terminate Azureus once a download has finished! **Leave it open until your Ratio is 1.0 or better. **A ratio of 1.0 means you have uploaded as much as you have downloaded. Anything below means that you are "leeching" (you behave in parasitic ways!) and not helping others. **Other users such as myself will regularly kick+ban and block the IP addresses of leeches if we detect them (it is possible for other users to see what ratio you have!).**

So in your own interest: **Don't be a parasite ... keep seeding** whatever you just downloaded and maintain a good ratio of **at least 1.0** ... 

Hope this helped.

---

### Post by mamboze on 2008-04-14
Thanks to you all for your friendly help. It is much appreciated. I'm a Ubuntu noob (and in several other areas too!!) but being a member of the Ubuntu community is fantastic; it is a great learning environment, I love it. 

Scorp123, I take your point about leeching. I'm not surprized people do it but why bother, it's no problem to leave the computer on-line, I wouldn't have thought. 

best regards

---

