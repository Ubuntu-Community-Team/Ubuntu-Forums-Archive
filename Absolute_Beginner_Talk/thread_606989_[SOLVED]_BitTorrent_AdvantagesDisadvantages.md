---
title: "[SOLVED] BitTorrent: Advantages/Disadvantages"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2007-11-08
I recall once setting up Bit Torrent in Windows. Then I read that a lot of BT sites were being "raided" for illegal content.  I deleted it!
I'm also under the impression that if BT is enabled that "other BT enabled PCs use a part of my bandwidth"

Of course I might be totally on the wrong side of the ball here.

I checked out: [http://www.bittorrent.com/dna/?csrc=splash](http://www.bittorrent.com/dna/?csrc=splash)

Where is says: Bit Torrent DNA is a content delivery service that uses a secure, private, managed peer network to power faster, more reliable, more efficient delivery of richer content. Bit Torrent DNA works with your existing CDN or origin servers, seamlessly accelerating your downloads or HTTP media streams.

With over 150 million clients downloaded, Bit Torrent is the consumer standard for software and content distribution on the Internet. Bit Torrent DNA extends the open Bit Torrent protocol into a managed platform for commercial-grade content delivery.

ummm... peer network. Would I need a firewall? I recall how my cable-modem light were always flashing even though I was not actively on the net in Windows. So I'd disable my LAN Card.

From: [http://en.wikipedia.org/wiki/BitTorrent](http://en.wikipedia.org/wiki/BitTorrent)
Limitations and security vulnerabilities

Bit Torrent does not offer its users anonymity. It is possible to obtain the IP addresses of all current, and possibly previous, participants in a swarm from the tracker. This may expose users with insecure systems to attacks.

As I see it:

Advantages: faster downloads. { True or False }
Disadvantages: Others using my bandwidth. { If I recall correctly, I saw a a message, similar to: Don't close Bit Torrent, keep the connection alive as long as possible }

So I'm looking for some feedback, should I use a torrent or not?
Should I install a firewall if I use it?  :confused:

---

### Post by P4man on 2007-11-08
First off, bittorrent is a protocol. It can be used for good or wrong, just like IRC, email, HTTP (web). You can download illegal stuff with HTTP just as well, I don't see anyone uninstall his browser because of that :p

That said ,its true  Bittorrent is often used to spread or obtain illegal content, warez, music, movies etc. That is only because it such a good protocol to handle large files. If HTTP where better, its what pirates would use :)

anyway, the idea behind bittorrent is that rather than having a single point from which everyone downloads (rapidly causing congestion at that point) is that everyone that downloads, also uploads to other downloaders at the same time. This spreads the bandwith requirements over everyone which makes a lot of sense.

Consider Ubuntu. When a new version is released, and tens of thousands want to download that 750 Mb file it causes massive problems for Canonical (and its mirrors). With bittorrent, I could seed Ubuntu from my home network, and millions could download it at the same speed as a single user. The more users download it, the more bandwidth the entire group ("swarm" in bt terms) gets.

> 
Advantages: faster downloads. { True or False }

Not necessarily, but often, yes. Especially in cases like a new Ubuntu release where everyone wants to download at the same time, you could expect traditional servers to fall over, where a bt network only gets better as more people download (and upload).

> Disadvantages: Others using my bandwidth. { If I recall correctly, I saw a a message, similar to: Don't close Bit Torrent, keep the connection alive as long as possible }

You are using other people's bandwidth when you download, its is expected you give back as well. To be fair, you should aim for a share ratio of around  1/1. Meaning, you upload as much as you downloaded. Most connections will download much faster than upload, so when you have downloaded your 750Mb file, you might only have uploaded 75Mb. For BT networks to keep working, people should keep their bt client open to seed (upload) until they have reached that ratio. So yes, in total you will have used 1.5GB traffic to download 750Mb. If your ISP doesnt put too severe caps on your bandwidth it shouldnt be a problem. And if your ISP does that, no one is going to kill  you if you do  stop uploading  ;)

---

### Post by Bruce M. on 2007-11-08
Hi P4man

> **P4man said:**
> First off, bittorrent is a protocol. It can be used for good or wrong, just like IRC, email, HTTP (web). You can download illegal stuff with HTTP just as well, I don't see anyone uninstall his browser because of that  :p

OK, have to agree there, I left my browser, just BT was deleted.  I thought the "whole concept of BT was "illegal" at that time.

> **P4man said:**
> That said ,its true  Bittorrent is often used to spread or obtain illegal content, warez, music, movies etc. That is only because it such a good protocol to handle large files. If HTTP where better, its what pirates would use :)

And that's probably why I thought that.

> **P4man said:**
> anyway, the idea behind bittorrent is that rather than having a single point from which everyone downloads (rapidly causing congestion at that point) is that everyone that downloads, also uploads to other downloaders at the same time. This spreads the bandwith requirements over everyone which makes a lot of sense.

Consider Ubuntu. When a new version is released, and tens of thousands want to download that 750 Mb file it causes massive problems for Canonical (and its mirrors). With bittorrent, I could seed Ubuntu from my home network, and millions could download it at the same speed as a single user. The more users download it, the more bandwidth the entire group ("swarm" in bt terms) gets.

Not necessarily, but often, yes. Especially in cases like a new Ubuntu release where everyone wants to download at the same time, you could expect traditional servers to fall over, where a bt network only gets better as more people download (and upload).

You are using other people's bandwidth when you download, its is expected you give back as well. To be fair, you should aim for a share ratio of around  1/1. Meaning, you upload as much as you downloaded. Most connections will download much faster than upload, so when you have downloaded your 750Mb file, you might only have uploaded 75Mb. For BT networks to keep working, people should keep their bt client open to seed (upload) until they have reached that ratio. So yes, in total you will have used 1.5GB traffic to download 750Mb. If your ISP doesnt put too severe caps on your bandwidth it shouldnt be a problem. And if your ISP does that, no one is going to kill  you if you do  stop uploading  ;)

This is the [COLOR="Orange"]**Jackpot**[/COLOR] and makes a lot of sense.
Now to check out what my ISP considers my limits, and learn HowTo BitTorrent.

Interesting how my first impression of BT was so negative!

---

### Post by P4man on 2007-11-08
Using it is really simple, setting it up might be a bit more difficult but only if you are behind a NAT router. Then you may have to configure some port forwarding.

As client, I would suggest Bittornado. Light weight, very easy to use, yet not missing any of the most important features. Azureus is also very popular one, but its a resource hog, and doesn't play nice with gutsy.

How to use it ? simple, if you see a bt download (like for ubuntu), just click the link. This will download a small text file, the so called "torrent" file. This text file contains some meta data, describing the actual file(s)  (in our example, the ubuntu iso), its size, the tracker (=server that does the bookkeeping between all the clients) etc. 

Save it somewhere, or open it straight away with your chosen bt client. This client will then ask you where to put the actual file, and thats it really. It will start downloading. Might be slow initially, but should speed up after a few minutes at most.

If after some minutes it is still slow, and the "smiley" is yellow or red, rather than green, report back, you may have to do some configuration of your router.

---

### Post by dfreer on 2007-11-08
Bittorrent is great, basically to add what the above posters said, I like to think of it as a "counterpart" or inverse of the standard HTTP download.

Lots of people downloading via HTTP -> Slow download speeds
Few people downloading via HTTP - > Fast download speeds
Lots of people downloading via Bittorrent -> Fast download speeds
Few people downloading via Bittorrent -> Slow download speeds

The main problem with bittorrent right now, is that unpopular files or files that no one needs can become extremely difficult, if not impossible to download. For example, I once tried downloading "a completely legal copy of something incredibly boring ;) ", got 80% of the download completed only to realize that out of the 4 peers that I was downloading with, none of us had the complete file. So we all ended up stuck at 80% waiting for someone to come along with a complete copy (a seeder), eventually I gave up.
This is why it is requested (and on some trackers, enforced) that you "leave the program running", so that once you have the complete file you can in turn pass it on to others. It's only polite, and you can leave it on at night when you are not using it, and turn it off during the day when you are so that your bandwidth won't suffer.

But for popular files, such as Ubuntu Gutsy on release day, the download speeds are *incredibly* fast because of all of the peers/seeds that I can download from.

EDIT: I like to use torrentflux on a server, that way I only have to open the ports for one PC, and I can turn off my laptop with my downloads still running.

---

### Post by P4man on 2007-11-08
> **dfreer said:**
> 
The main problem with bittorrent right now, is that unpopular files or files that no one needs can become extremely difficult, if not impossible to download..

True,  although that is more likely to happen with some exotic warez stuff, than say Ubuntu ISO's. Since most legal content will have a  permanent seeder,  at least 1 machine always has all the bits. Usually that machine will also have enough bandwidth to guarantee at least a few fast downloads, so even if you are the only one downloading, it should be fast.

Some other problems that exist:
- some ISPs deliberately  slow down bittorrent traffic (and similar peer2peer protocols).  The inquirer.net had an article on that recently, don't recall which ISPs they where, but rather big ones. That sucks very hard, especially if you do intend to use it for legal purposes.
- There are companies that "protect" the business of movie/music industry by deliberately corrupting illegal torrents. Again, this won't affect your ubuntu ISO download, but they do send false packets for torrents that contain DVD rips, music etc to render the network useless. Well, they try at least. Of course, they will also try to get your IP and if possible sue you for downloading illegal material, but again, that is not something you should fear if you download legal stuff.

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> Using it is really simple, setting it up might be a bit more difficult but only if you are behind a NAT router. Then you may have to configure some port forwarding.

No router, no wireless no nothing, (OK, bad grammar) just a simple PC (see sig) with a cable-modem. No "power" this or that  :lol:

> **P4man said:**
> As client, I would suggest Bittornado. Light weight, very easy to use, yet not missing any of the most important features. Azureus is also very popular one, but its a resource hog, and doesn't play nice with gutsy.

Again see my sig:  No Gutsy (yet).  From what you say, I'll skip Azureus.  What's wrong with the default BitTorrent?

> **P4man said:**
> How to use it ? simple, if you see a bt download (like for ubuntu), just click the link. This will download a small text file, the so called "torrent" file. This text file contains some meta data, describing the actual file(s)  (in our example, the ubuntu iso), its size, the tracker (=server that does the bookkeeping between all the clients) etc. 

Save it somewhere, or open it straight away with your chosen bt client. This client will then ask you where to put the actual file, and thats it really. It will start downloading. Might be slow initially, but should speed up after a few minutes at most.

If after some minutes it is still slow, and the "smiley" is yellow or red, rather than green, report back, you may have to do some configuration of your router.

  That sounds easy enough.  Don't I have to start the BT client first?

  Oh, I don't plan on using it in the immediate future (minutes, hours or days) I'm checking things out because I will be going for Gutsy.
  Also I guess not all programs can be had with a torrent.

  I am learning though, and that's a good thing.  :biggrin:

---

### Post by bionnaki on 2007-11-08
bittorrent rules. find yourself a private tracker and decent client (deluge, ktorrent, azureus, transmission are recommended) and enjoy. I've been using torrents for about 5 years and I have not had any legal trouble (live in the US).

---

### Post by bionnaki on 2007-11-08
bittornado? are you kidding me? that sucks.

listen just go here and install the correct .deb: [http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

---

### Post by Bruce M. on 2007-11-08
> **dfreer said:**
> Bittorrent is great, basically to add what the above posters said, I like to think of it as a "counterpart" or inverse of the standard HTTP download.

Lots of people downloading via HTTP -> Slow download speeds
Few people downloading via HTTP - > Fast download speeds
Lots of people downloading via Bittorrent -> Fast download speeds
Few people downloading via Bittorrent -> Slow download speeds

  Filed away with other new stuff learned today.

> **dfreer said:**
> The main problem with bittorrent right now, is that unpopular files or files that no one needs can become extremely difficult, if not impossible to download. For example, I once tried downloading "a completely legal copy of something incredibly boring ;) ", got 80% of the download completed only to realize that out of the 4 peers that I was downloading with, none of us had the complete file. So we all ended up stuck at 80% waiting for someone to come along with a complete copy (a seeder), eventually I gave up.

 Couldn't you get it via regular HTTP download?

> **dfreer said:**
> This is why it is requested (and on some trackers, enforced) that you "leave the program running", 

How can they "enforce" that?

> **dfreer said:**
> But for popular files, such as Ubuntu Gutsy on release day, the download speeds are *incredibly* fast because of all of the peers/seeds that I can download from.

  This I like, although I would think the RUSH for Gutsy is gone now.   ;(
  Thinking about: ***incredibly* fast download speeds.**

> **dfreer said:**
> EDIT: I like to use torrentflux on a server, that way I only have to open the ports for one PC, and I can turn off my laptop with my downloads still running.

  Nope, no server here.  My :shock:s are bigger than my wallet.  :oops:

---

### Post by Bruce M. on 2007-11-08
> **bionnaki said:**
> bittorrent rules. find yourself a private tracker and decent client (deluge, ktorrent, azureus, transmission are recommended) and enjoy. I've been using torrents for about 5 years and I have not had any legal trouble (live in the US).

:confused:  --- A private tracker ??

More to this than I figured.
Please explain.

---

### Post by akiratheoni on 2007-11-08
> **Bruce M. said:**
>  Couldn't you get it via regular HTTP download?

I don't know if it's just me, but if I'm getting a torrent of something that's "a completely legal copy of something incredibly boring" then there's probably NOT an http download available or if it is, it's probably on a website that ends in .biz or is in a foreign language. :)

---

### Post by P4man on 2007-11-08
> **Bruce M. said:**
> :confused:  --- A private tracker ??

More to this than I figured.
Please explain.

A private tracker is a tracker not everyone can see.  A private tracker gives you more security from police/fbi etc if you want to download illegal stuff. Since you seem to be very reluctant of doing anything illegal, it is not something you will either need or encounter :)

---

### Post by Bruce M. on 2007-11-08
> **bionnaki said:**
> bittornado? are you kidding me? that sucks.

listen just go here and install the correct .deb: [http://deluge-torrent.org/downloads-ubuntu](http://deluge-torrent.org/downloads-ubuntu)

Ooops, play fair guys, or you'll go on Santa's "Naughty List".  :)

Besides, everyone has their preferences, and two were suggested, Bittornado & Azureus.

In the end, it's my choice as to what to use anyway   :popcorn:

---

### Post by akiratheoni on 2007-11-08
> **Bruce M. said:**
> In the end, it's my choice as to what to use anyway   :popcorn:

Which is the downright beauty of Linux :)

---

### Post by P4man on 2007-11-08
> Again see my sig:  No Gutsy (yet).  From what you say, I'll skip Azureus.  What's wrong with the default BitTorrent?

Maybe nothing, but I couldnt figure out how to make it resume a download if I had to reboot/shut down before the download was complete. Since there are countless BT clients out there, I wasn't going to look for it very hard, and just installed another one.

>  That sounds easy enough.  Don't I have to start the BT client first?

No. The file you download (the .torrernt file) will be associated with your torrent client. Like downloading a PDF, you don't need to start your viewer first either; your browser will ask what app you want to use with the file, and will suggest your default BT client.
> 

 Oh, I don't plan on using it in the immediate future (minutes, hours or days) I'm checking things out because I will be going for Gutsy.
  Also I guess not all programs can be had with a torrent.

Well... not legally, but Illegally you can find more software than on Amazon I think :)

But iIts becoming more popular, for obvious reasons, if you are a software company (even more so when you are none profit, or a developer with an open source project), you don't need an expensive/fast server to  distribute your software. You can distribute from your home machine and still allow thousands of people to download it at good speed.

Also some browsers (Opera) have bittorrent capability built-in. No doubt firefox will integrate it too one day, and even MS is looking at peer2peer to distribute its patches and stuff.

edit: media companies are starting to use it too, letting you legally download and/or watch (DRM infected) movies using P2P.

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> A private tracker is a tracker not everyone can see.  A private tracker gives you more security from police/fbi etc if you want to download illegal stuff. Since you seem to be very reluctant of doing anything illegal, it is not something you will either need or encounter :)

  I'm not into music or movies so I'm not interested in that area at all.  I started this thread because BitTorrent comes with Ubuntu and my first reaction was to:

Edit Menus>Internet and unclick it.

  Now after reading the Forums and Questions I started getting curious about it.
  It's like you said in your first post here:

> First off, bittorrent is a protocol. It can be used for good or wrong, just like IRC, email, HTTP (web). You can download illegal stuff with HTTP just as well, I don't see anyone uninstall his browser because of that

  I'm learning the good points here.  And maybe it will shorten my 12 hour download time for Gutsy to ... what?  11 hours and 30 minutes?   :lolflag:

---

### Post by mivo on 2007-11-08
For me, the real advantage of bittorrent is that I can always easily pause a download and resume it at a later time. Also disconnections don't cause any real troubles. There are download managers for HTTP downloads, but they are less reliable in my experience. My connection is relatively slow due to living in a remote area (DSL with 384kbit, so 45k/s), so the ability to pause and resume downloads is important to me. Also, I think it's a good concept to "give back" some bandwidth, too. It's not a free resource.

---

### Post by P4man on 2007-11-08
> **Bruce M. said:**
>  And maybe it will shorten my 12 hour download time for Gutsy to ... what?  11 hours and 30 minutes?   :lolflag:

No protocol can increase download speeds beyond what your connection is (or how crappy or good your ISP is). If downloading ubuntu took you 12 hours because the ubuntu servers where overloaded, bitorrent would help. But if you are on dialup, or have a horrible ISP, bittorrent ain't goinna do miracles.

Generally though, popular torrents will pretty much max out your connection speed, which is more than can be said about most HTTP download sites.

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> Maybe nothing, but I couldnt figure out how to make it resume a download if I had to reboot/shut down before the download was complete. Since there are countless BT clients out there, I wasn't going to look for it very hard, and just installed another one.

I remember reading that somewhere too.

> **P4man said:**
> No. The file you download (the .torrernt file) will be associated with your torrent client. Like downloading a PDF, you don't need to start your viewer first either; your browser will ask what app you want to use with the file, and will suggest your default BT client.

Oh, if BitTorrent comes with Ubuntu, won't that be the default?
I just learned how to make Thunar the default over Nautalus yeaterday.


> **P4man said:**
> Well... not legally, but Illegally you can find more software than on Amazon I think :)

Of this I have no doubt.

> **P4man said:**
> But iIts becoming more popular, for obvious reasons, if you are a software company (even more so when you are none profit, or a developer with an open source project), you don't need an expensive/fast server to  distribute your software. You can distribute from your home machine and still allow thousands of people to download it at good speed.

Yea, that has to be a good thing.

> **P4man said:**
> Also some browsers (Opera) have bittorrent capability built-in. No doubt firefox will integrate it too one day, and even MS is looking at peer2peer to distribute its patches and stuff.

I wouldn't trust the MS P2P at all.  I've lost ALL faith in that area.

> **P4man said:**
> edit: media companies are starting to use it too, letting you legally download and/or watch (DRM infected) movies using P2P.

DRM .... Digital Rights something or other.  Like "Copyright", right?

---

### Post by AndyCooll on 2007-11-08
> **Bruce M. said:**
> Ooops, play fair guys, or you'll go on Santa's "Naughty List".  :)

Besides, everyone has their preferences, and two were suggested, Bittornado & Azureus.

In the end, it's my choice as to what to use anyway   :popcorn:

BT is indeed an excellent way for getting hold of files, especially large ones. I use it all the time to download distros.

I disagree with the views expressed about Azureus, IMHO it beats the pants of all other BT clients. People say its a memory hog but I have never felt this to be the case. Having said that my pc has 2gb RAM so maybe I'm less llikely to notice.. There's also actually a BT client installed by default in Ubuntu, though it is rather limited. 

There is also a thread on here somewhere which discusses different BitTorrent clients, and as you might gather there a whole range of viewpoints. My advice is to try a few, and see which one you prefer. 

:cool:

---

### Post by P4man on 2007-11-08
> **Bruce M. said:**
> I

DRM .... Digital Rights something or other.  Like "Copyright", right?

Digital Rights Management. Technology that disallows you to do stuff with your own property. An example would be special movie files that can only be played twice, then the file becomes useless. Or that only can be played back on your computer, and no other machine. Think Apple iTunes.

As with most technology, also DRM can be used for good and for bad. And like most pirates use bitorrent technology for "bad", most media companies use DRM in that way too, with incredbily restrictives schemes. 

Its this technology that ensures you can not make a backup or even play back your legally purchased blueray disk on your computer or tv because the DRM technology sees something it doesnt know or trust, that might in theory be used to make a copy, and therefore it refuses to play at all.

More info here:
[http://en.wikipedia.org/wiki/Digital_rights_management](http://en.wikipedia.org/wiki/Digital_rights_management)

BTW, DRM and Linux (open source) don't mix well. Totally opposing philosophies. Vista is the king of DRM

---

### Post by Bruce M. on 2007-11-08
> **mivo said:**
> For me, the real advantage of bittorrent is that I can always easily pause a download and resume it at a later time. Also disconnections don't cause any real troubles. There are download managers for HTTP downloads, but they are less reliable in my experience. My connection is relatively slow due to living in a remote area (DSL with 384kbit, so 45k/s), so the ability to pause and resume downloads is important to me. Also, I think it's a good concept to "give back" some bandwidth, too. It's not a free resource.

Hi mivo
Do you use the default BitTorrent?

> pause a download and resume it at a later time

THAT looks interesting!

I'm connected with a Cable Modem (100 Mb/s) so that is even slower My transfer rates start at about 32 +/- KB/sec and drop down to 14 +/- KB/sec.  That's why I'm asking about BitTorrent

---

### Post by Officer Dibble on 2007-11-08
There are a fair number of legal torrent sites out there... for example:

[http://www.azureuswiki.com/index.php/Legal_torrent_sites](http://www.azureuswiki.com/index.php/Legal_torrent_sites)

... and I recently downloaded a great Sherlock Holmes film from here recently:

[http://www.legaltorrents.com/](http://www.legaltorrents.com/)

But as you'll see it's down for revamp at the moment... keep checking it though. :)

---

### Post by Bruce M. on 2007-11-08
> **AndyCooll said:**
> BT is indeed an excellent way for getting hold of files, especially large ones. I use it all the time to download distros.

I disagree with the views expressed about Azureus, IMHO it beats the pants of all other BT clients. People say its a memory hog but I have never felt this to be the case. Having said that my pc has 2gb RAM so maybe I'm less llikely to notice.. There's also actually a BT client installed by default in Ubuntu, though it is rather limited. 

There is also a thread on here somewhere which discusses different BitTorrent clients, and as you might gather there a whole range of viewpoints. My advice is to try a few, and see which one you prefer. 

:cool:

I've been quietly collecting a list of clients here to look at.
2 GB RAM! -  [-o<  I need a new computer!!!  And I thought 512 was good.  :(

---

### Post by Bruce M. on 2007-11-08
> **Officer Dibble said:**
> There are a fair number of legal torrent sites out there... for example:

[http://www.azureuswiki.com/index.php/Legal_torrent_sites](http://www.azureuswiki.com/index.php/Legal_torrent_sites)

... and I recently downloaded a great Sherlock Holmes film from here recently:

[http://www.legaltorrents.com/](http://www.legaltorrents.com/)

But as you'll see it's down for revamp at the moment... keep checking it though. :)

Geeeze!! I had NO idea!  Thanks, just maybe I'll play a while before trying for Gutsy.

I've been missing out on a LOT of fun.

---

### Post by P4man on 2007-11-08
> **Bruce M. said:**
> I've been quietly collecting a list of clients here to look at.
2 GB RAM! -  [-o<  I need a new computer!!!  And I thought 512 was good.  :(

For most things, 512 is plenty with Ubuntu. I have 2GB as well, but since I switched from windows to ubuntu, I dont think Ive often used more than 512. 

Still, Azureus will happily take away 100 or more Mb, I saw in your sig you had 512Mb, thats one of the reasons I didnt recommend it. Its a big, feature packed app, but if you are not hardcore downloader, you won't miss (m)any of its features.

---

### Post by atomkarinca on 2007-11-08
if you want a lightweight torrent client then i would suggest ktorrent or deluge torrent

> sudo apt-get install ktorrent

or

sudo apt-get install deluge-torrent

ktorrent is my choice of these two, though.

---

### Post by mivo on 2007-11-08
Just to chip in a number for comparison: [Deluge]("http://deluge-torrent.org") uses about 22 MB RAM. And I agree, this box here has 3 GB RAM, and I have never seen it use more than 1 GB in Ubuntu even though I make fair use of eye candy and "stuff".

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> Digital Rights Management.

More info here:
[http://en.wikipedia.org/wiki/Digital_rights_management](http://en.wikipedia.org/wiki/Digital_rights_management)

BTW, DRM and Linux (open source) don't mix well. Totally opposing philosophies. Vista is the king of DRM

Shortened your quote ... I was missing the "Management" part of it.  The "basic" concept of DRM I understood.
And from what I've read ( a little ), MS has started sneaking this DRM stuff into XP's upgrades too.  Don't quote me on that though.

---

### Post by P4man on 2007-11-08
> **Bruce M. said:**
> 
And from what I've read ( a little ), MS has started sneaking this DRM stuff into XP's upgrades too.  Don't quote me on that though.

I just did :p

---

### Post by wog on 2007-11-08
A couple of points I don't see mentioned.

On BT (the default torrent program in Ubuntu), to resume a file after breaking off at some point, open the torrent file you used to start your download in the first place. When BT asks where to save the file, point it at the same directory you downloaded to before. BT detects the file automagically, checks to see how much of the file is actually there, and resumes.

Another point about internet connections in general, your modem will check in from time to time to make sure the connection is still live, so activity or lack of activity is not a way to know whether your system is being accessed. However, that said, if your system is being accessed, the throughput will be much higher than if it is not.

Lastly, firewalls are used to protect your system and throughput from people who use BT-related programs (or blind luck) to find your IP address and attack your system directly. If you have no router between you and the modem, you'll need a software firewall. I don't remember the Linux versions offhand, but browsing Synaptic or Googling for it can probably give you more than a few options. On my Windows machines I use ZoneAlarm, even though it can be a little fiddly.

I hope that helps someone. :D

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> For most things, 512 is plenty with Ubuntu. I have 2GB as well, but since I switched from windows to ubuntu, I dont think Ive often used more than 512.

Breathing easier now.    :)

> **P4man said:**
> Still, Azureus will happily take away 100 or more Mb, I saw in your sig you had 512Mb, thats one of the reasons I didnt recommend it. Its a big, feature packed app, but if you are not hardcore downloader, you won't miss (m)any of its features.

Have used BT once in Windows, saw my lights blinking after I got of the net and figured NOT GOOD!  I was wrong.  There's that my old "mindset" in action again.

---

### Post by Bruce M. on 2007-11-08
> **atomkarinca said:**
> if you want a lightweight torrent client then i would suggest ktorrent or deluge torrent

ktorrent is my choice of these two, though.

One of these would probably fit my ( hey, I don't have to say: wallet with Linux ) machine better   :)

Thanks...  for the commands as well.

---

### Post by mivo on 2007-11-08
> **wog said:**
> AI don't remember the Linux versions offhand, but browsing Synaptic or Googling for it can probably give you more than a few options.

Ubuntu comes with iptables, but without any rules, so it is theoretically wide open, except that it does not run vulnerable services out of the box. However, it really is a good idea to grab the **firestarter** package from the repository and run the wizard. Firestarter is only a GUI for iptables, it is not a firewall itself (so does not need to be kept open after the configuration is done).

---

### Post by Bruce M. on 2007-11-08
> **mivo said:**
> Just to chip in a number for comparison: [Deluge]("http://deluge-torrent.org") uses about 22 MB RAM. And I agree, this box here has 3 GB RAM, and I have never seen it use more than 1 GB in Ubuntu even though I make fair use of eye candy and "stuff".

3GIG!  {crying in my coffee} so much for the 640K is enough for anyone!

But 22MB doesn't look TOO bad!  I have to get myself a "memory usage" checker-upper.

:lolflag:

---

### Post by Bruce M. on 2007-11-08
> **P4man said:**
> I just did :p

That's NOT what I meant and you know it.
Now go to your room and write:

> I will not quote Bruce when he says don't quote me on that

100 times!   :lolflag:

NO ...  I take that back ... I do not want to see it here 100 times!

---

### Post by mivo on 2007-11-08
> **Bruce M. said:**
> But 22MB doesn't look TOO bad!  I have to get myself a "memory usage" checker-upper.

There is one built into your Ubuntu already! :)  Just go to *System -> Administration -> System Monitor*, and select the "Processes" tab. For even more information, open a terminal window and type **sudo top**.  See, Ubuntu hides nothing from you!

---

### Post by dfreer on 2007-11-08
> **Bruce M. said:**
> 
[QUOTE=dfreer;3732738]This is why it is requested (and on some trackers, enforced) that you "leave the program running", so that once you have the complete file you can in turn pass it on to others.

How can they "enforce" that?
[/QUOTE]

Well, this is the way one of my private trackers enforce sharing. I had to register with a username/password, which allows me to access the torrents provided by normal users. When I decide on which torrent I want to download, I click on a download link, which consists of using HTTP to download a small .torrent file (a quick look shows some of mine being ~20 kb. From what I understand of it, a normal .torrent will pretty much just a file that contains
(1). The address of the tracker. The tracker is a server that maintains connection information about seeds/peers involved with your .torrent.
(2). List of all the files associated with that .torrent, along with a hash of some sort. For example, a 
.torrent for an Ubuntu Live CD would probably have just one file, the ubuntu-liveCD.iso itself.).

For my private tracker, this .torrent is generated on-the-fly just for me, and also contains some other unique information, namely my username on the site and my current external IP address (not quite as simple as that in actuality). I then load this .torrent into my bittorrent client, which when started will connect to the tracker. The .torrent file in this case validates that I have permission to download (since this is a private tracker), and keeps track of how much I download/upload. 

One of the rules for the private tracker I use, is that users must have a download/upload ratio of 1.5:1, so for every 1.5 GB I download, I must have uploaded 1 GB to other users. After a probationary period (after I've downloaded more than 5 GB's in my case), if my ratio is too low my username/IP address is denied access to the tracker, preventing me from getting the IP addresses of my peers which prevents me from downloading any more files.

Public trackers generally don't monitor download/upload ratios, but it is generally considered to be bad form to only download and to limit your uploads (hence the title "leechers"). Kinda like talking in ALL CAPS in a forum, understandably at times, but you shouldn't do it all the time or even most of the time. 

> **Bruce M. said:**
> Couldn't you get it via regular HTTP download?

Not always, I have seen some sites provide prefectly legal files only through bittorrent, simply to save bandwidth. A site should IMO always provide two links at least, one for HTTP and one for bittorrent. In other cases, the files may be so large that I do not want to even attempt downloading them through a traditional method, I once downloaded the entire Debian CD set (approx 20 CD's I do believe?) **over a 56k modem**. You should've seen me freak out when anyone so much *looked* at the computer that was downloading them... now I wouldn't even consider using HTTP for such a task unless absolutely needed.

Now that I've gone on forever, I did want to point out one other feature that I don't think has been mentioned: Most bittorrent clients allow you to select which files in any given torrent you actually want to download. Let's say there was a mega-collection of all of the Ubuntu varients (ubuntu, kubuntu, xubuntu, etc). But you only want to download kubuntu and ubuntu, and none of the others. You can download the .torrent associated for the entire collection, and just select those two. The download will proceed, and you can even seed just those two files if you wish (although most tracker will still list you as leeching instead of seeding, because you don't have the entire collection. This will not be a problem in most cases). In the future, you can even go back and download ones you missed without any issues.

---

### Post by Bruce M. on 2007-11-09
I had to drop out like a hot potato yesterday, something came up that needed attention.  But I'm back again and been doing some reading.
Time to reply...

---

### Post by Bruce M. on 2007-11-09
Hi wog, thanks for your comments.

> **wog said:**
> A couple of points I don't see mentioned.

On BT (the default torrent program in Ubuntu), to resume a file after breaking off at some point, open the torrent file you used to start your download in the first place. When BT asks where to save the file, point it at the same directory you downloaded to before. BT detects the file automagically, checks to see how much of the file is actually there, and resumes.

Well, that's easy, I have a (leftover from the old days) ZIP folder that I download everything to.

> **wog said:**
> Another point about internet connections in general, your modem will check in from time to time to make sure the connection is still live, so activity or lack of activity is not a way to know whether your system is being accessed. However, that said, if your system is being accessed, the throughput will be much higher than if it is not.

Yes, I realize that too, plus Thunderbird is configured to get check mail at regular intervals, as well as the panel app "Weather Report".  I would never have allowed this type of activity when in Windows.  In fact it was out habit to "disconnect" our LAN card in windows when not using the net.  But those are intermittent and not solid blinking as I saw when I used BT.

> **wog said:**
> Lastly, firewalls are used to protect your system and throughput from people who use BT-related programs (or blind luck) to find your IP address and attack your system directly. If you have no router between you and the modem, you'll need a software firewall. I don't remember the Linux versions offhand, but browsing Synaptic or Googling for it can probably give you more than a few options. On my Windows machines I use ZoneAlarm, even though it can be a little fiddly.

I hope that helps someone. :D

**Firestarter** is the firewall in Synaptic.  But I was told it wasn't necessary with Ubuntu Desktop.  Recommended if you run a server.
With windows I started with ZoneAlarm, and switched to COMODO.  I liked it better.
If you're still using windows check out [[COLOR="Blue"]ZonedOut.[/COLOR]]("http://www.funkytoad.com/content/view/15/33/")  Not a firewall, it put 2600+ restricted sites in MSIE's Restricted Zones.  Check out Eric Howes lists mentioned at the site.

---

### Post by Bruce M. on 2007-11-09
Hi mivo, welcome back.

> **mivo said:**
> Ubuntu comes with iptables, but without any rules, so it is theoretically wide open, except that it does not run vulnerable services out of the box. However, it really is a good idea to grab the **firestarter** package from the repository and run the wizard. Firestarter is only a GUI for iptables, it is not a firewall itself (so does not need to be kept open after the configuration is done).

  Now this is interesting.  When I first switched to Linux I started asking questions; ***Solved  Question #12839, asked on 2007-09-05  by Bruce M. Firewall and antivirus***

  Where I was told I don't need a firewall.  But this iptables is already here without rules.  If I don't use a BT client is it recommended to get Firestarter and set rules?

  Correct me if I'm wrong, but since I started using Ubuntu I was under the impression that all ports are closed unless **"I"** decide to go on the net and do something.

  I understand a bit ( no pun intended ) more now about how a BT client works, leaving a port ( or ports ) open to allow it to do it's work.  But wouldn't that be restricted to "the file" in question and nothing else.

---

### Post by Bruce M. on 2007-11-09
> **mivo said:**
> There is one built into your Ubuntu already! :)  Just go to *System -> Administration -> System Monitor*, and select the "Processes" tab. For even more information, open a terminal window and type **sudo top**.  See, Ubuntu hides nothing from you!

Well, I'll be a .... would you look at that! 
System Monitor tells me I'm using:

User Memory:  192.7 MB of 502.7 MB RAM
Used swap:  31.1 MB of 1.0GB

Hey ... I have 512MB RAM!  What's up?

And sudo top:  THIS I LIKE!!!!!

top - 13:45:35 up  4:12,  2 users,  load average: 0.46, 0.59, 0.53
Tasks:  97 total,   4 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.9%us,  2.0%sy,  0.3%ni, 86.1%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:    514760k total,   507416k used,     7344k free,    39300k buffers
Swap:  1100412k total,    31808k used,  1068604k free,   267184k cached

¿2 users? ...  :confused: 

Thanks mivo

Oh, I have a second workspace open   :)

BTW, for Tasks: thats 92 sleeping+wife

---

### Post by Bruce M. on 2007-11-09
Hi dfreer ... trimmed out some

> **dfreer said:**
> One of the rules for the private tracker I use, is that users must have a download/upload ratio of 1.5:1, so for every 1.5 GB I download, I must have uploaded 1 GB to other users. After a probationary period (after I've downloaded more than 5 GB's in my case), if my ratio is too low my username/IP address is denied access to the tracker, preventing me from getting the IP addresses of my peers which prevents me from downloading any more files.

OK, I'm getting idea.  But I don't think I'll be needing a private tracker.   :)

> **dfreer said:**
> Public trackers generally don't monitor download/upload ratios, but it is generally considered to be bad form to only download and to limit your uploads (hence the title "leechers"). Kinda like talking in ALL CAPS in a forum, understandably at times, but you shouldn't do it all the time or even most of the time.

leecher ... yup, that's me!

NO, seriously, if I am convinced that it will not harm my PC, I won't have a problem "giving it back"

> **dfreer said:**
> I once downloaded the entire Debian CD set (approx 20 CD's I do believe?) **over a 56k modem**. You should've seen me freak out when anyone so much *looked* at the computer that was downloading them... now I wouldn't even consider using HTTP for such a task unless absolutely needed.

Had to bite my tongue so as not to wake up my wife (taking a siesta) from laughing.  That must have taken a good week!

> **dfreer said:**
> Now that I've gone on forever, I did want to point out one other feature that I don't think has been mentioned: Most bittorrent clients allow you to select which files in any given torrent you actually want to download. Let's say there was a mega-collection of all of the Ubuntu varients (ubuntu, kubuntu, xubuntu, etc). But you only want to download kubuntu and ubuntu, and none of the others. You can download the .torrent associated for the entire collection, and just select those two. The download will proceed, and you can even seed just those two files if you wish (although most tracker will still list you as leeching instead of seeding, because you don't have the entire collection. This will not be a problem in most cases). In the future, you can even go back and download ones you missed without any issues.

Personally, I think I'd go for one at a time and stay away from the "collections".  My wife likes to use the computer too!

This whole thread is an eye opener for me and I'm coming to the opinion that a BT client has a lot more advantages then disadavantages.

---

### Post by wog on 2007-11-10
> **Bruce M. said:**
> 
But those are intermittent and not solid blinking as I saw when I used BT.

Well, of **course** when you're using BT you'll get a higher level of activity. BT is making **your** copy of the file available for others to download, just as others are sharing their copy for you to get it from **them**.

Not to be insulting, but basically, downloading with BT is a matter of personal honor. In order to continue to make a file available, you have to share, and some people aren't into sharing. If there's a file which has only one or two distributed copies, and no other seeds, and you don't share, you're basically killing the file so no-one else can download.

Luckily, BT also allows you to share a file at times other than when you've first downloaded, so if you haven't shared a file back out but you can't do it right then, you can always do it later, provided not too much time has passed.

---

### Post by Bruce M. on 2007-11-10
Hi wog, welcome back.

> **wog said:**
> Well, of **course** when you're using BT you'll get a higher level of activity. BT is making **your** copy of the file available for others to download, just as others are sharing their copy for you to get it from **them**.

OK, let talk example and see how close I am to getting this.

I start downloading Gutsy, along with 100 others using a BT client.  We're sharing pieces of the 700MB ISO file as we go.  Lets assume I'm the 25th person to get the complete file, there are still 75 more people out there collecting from us.  I contune to use my computer for another 2 hours, "feeding" these people.  ( I'm guessing here, but it is at this point that "leeches" would close down their BT client. Correct? ) During this 2 hours another 30 start downloading, some will obviously be collecting chunks from me as well.  At this point I turn my computer off for the night.  Breaking the BT clients connection.  I'm out of the "loop".

Next morning I start my PC and collect my mail, maybe I answer one or two mails in the process, but I don't start my BT client.

What happens here?  Does my BT client recognize that I have the Gutsy ISO file and start delivering pieces automatically to people that are downloading it?  Or do I have to start my BT client, and let it resume connections for requests?

And a BIGGIE for me.  If I have two or three files that I downloaded via HTTP method, does my BT client share these as well if someone starts downloading them with a BT client?  Or is this "file sharing" restricted to the files I have downloaded in the past with my BT client?

> **wog said:**
> Not to be insulting, but basically, downloading with BT is a matter of personal honor. In order to continue to make a file available, you have to share, and some people aren't into sharing. If there's a file which has only one or two distributed copies, and no other seeds, and you don't share, you're basically killing the file so no-one else can download.

No insult taken, I'm in learning mode here.  And as I said before, if the rest of my system isn't going to be compromised, I'm not against sharing the files, "especially Ubuntu files".

> **wog said:**
> Luckily, BT also allows you to share a file at times other than when you've first downloaded, so if you haven't shared a file back out but you can't do it right then, you can always do it later, provided not too much time has passed.

Is this automatic, or something I must elect to do?

---

### Post by P4man on 2007-11-10
> **Bruce M. said:**
> 
What happens here?  Does my BT client recognize that I have the Gutsy ISO file and start delivering pieces automatically to people that are downloading it?  Or do I have to start my BT client, and let it resume connections for requests?

You have to restart the client before any uploading will happen. It depends on the client if you have to do anything after loading it, but without an action from you, nothing will happen.
> 
And a BIGGIE for me.  If I have two or three files that I downloaded via HTTP method, does my BT client share these as well if someone starts downloading them with a BT client?  Or is this "file sharing" restricted to the files I have downloaded in the past with my BT client?

It is strictly limited to the torrent files. Most clients will give you a list with all torrents you downloaded or are downloading, and which ones you are still uploading, and their upload ratio. SImpeler clients may not give you all that info, but then these also won't upload a damn thing unless you manually reopen the torrent file, at which point the program will reconnect to the "tracker" (server) and resume downloading (if you havent completed yet) and uploading (until you reach a preset ratio, or you cancel it)

Using bittorrent is much easier than reading about it or explaining it :)

---

### Post by Bruce M. on 2007-11-10
Hi again P4man

> **P4man said:**
> You have to restart the client before any uploading will happen. It depends on the client if you have to do anything after loading it, but without an action from you, nothing will happen.

Good to know  :)

> **P4man said:**
> It is strictly limited to the torrent files. Most clients will give you a list with all torrents you downloaded or are downloading, and which ones you are still uploading, and their upload ratio. SImpeler clients may not give you all that info, but then these also won't upload a damn thing unless you manually reopen the torrent file, at which point the program will reconnect to the "tracker" (server) and resume downloading (if you havent completed yet) and uploading (until you reach a preset ratio, or you cancel it)

Ok, now it's come down to which BT client to use.

> **P4man said:**
> Using bittorrent is much easier than reading about it or explaining it :)

Thanks P4man.

Now I'm going to find a client, and try a download of some type.  Since there were a couple of torrent sites recommended here I'll start there.

I'll come back and let everyone know how it went.  I'm sure some will be thinking. "Why?".  But keep in mind, it's my first kick at the can.  :lolflag:

---

### Post by rsambuca on 2007-11-10
Wow Bruce!  48 posts and counting before even starting.  I commend you on your thoroughness.  If everyone conducted their research like you prior to blindlessly jumping in, these forums would have **a lot** less threads!

Good luck with your torrents!

One thing I just wanted to mention that I haven't seen here.   Another benefit of using torrents is that the hash of each piece of the torrent is checked as you download it, so you are more likely to get an uncorrupted file than by regular http downloading.  If a piece fails the hash check, it is chucked out immediately and re-downloaded from somewhere else.

---

### Post by baybe1111 on 2007-11-10
OK, I see the advantages. I've followed the instructions above but I think I have a firewall problem with my modem. Its a GlobeSurfer II 7.2 connecting to the Virgin 3G/HSDPA network. I've tried to configure port forwarding via the menu on 192.168.1.1.

I set the connection settings/security/portforwarding/

local host: to my ip address from ifconfig (192.168.1.2)
protocol:any
forward to port: specify: somewhere aroound the 52000

Then I set gtk-gnutella to listen on the above port.

Then voilla- nothing happens. gtk-gnutella still says I'm firewalled and trying to download a torrent fails.

Help please.

---

### Post by P4man on 2007-11-11
Did you install a software firewall on your system ? 

 if your router supports it, try temporarily putting your ip in the DMZ zone, if that doesnt cure it, the problem is not with your router, but maybe the network (ISP) ? Try other ports then

From the gnutella faq:
> 
Why does gtk-gnutella claim it's firewalled when it's not?

gtk-gnutella needs to receive an incoming connection to determine if you can be reached from the outside. Until then, it's assumed that there's a firewall which blocks the configured listening TCP port. If you want to speed up the detection, use a web browser, telnet or similar and connect to the listening port from the outside. If the connection is refused or dropped, then you are very probably really unreachable due to a firewall which blocks the port, a misconfigured NAT or similar. You might want to try a different listening TCP port because some ISPs block the default Gnutella port (6346). 

---

### Post by wog on 2007-11-11
baybe1111, just for future reference, the best place to put a problem with hardware is in the main newbie area, unassociated with anyone else's thread. You are more likely to get an answer which is dedicated to your problem, and are less likely to have your question be ignored by knowledgeable people.

Not that your problem is being ignored here, mind you... :)

---

### Post by Bruce M. on 2007-11-11
Hi rsambuca.

Calgary huh!  I have some fond memories (faded a bit) of the Stampede back in the mid 50's to early 60's.  I met the Cisco Kid and Poncho, Roy Rodgers and Dale Evens,  Bat Masterson, and more that I can't recall.  It was a kids dream come true.   :)

> **rsambuca said:**
> Wow Bruce!  48 posts and counting before even starting.  I commend you on your thoroughness.  If everyone conducted their research like you prior to blindlessly jumping in, these forums would have **a lot** less threads!

Good luck with your torrents!

Shhhhhh, don't tell anyone, but it's probably more my stubborn nature.

> **rsambuca said:**
> One thing I just wanted to mention that I haven't seen here.   Another benefit of using torrents is that the hash of each piece of the torrent is checked as you download it, so you are more likely to get an uncorrupted file than by regular http downloading.  If a piece fails the hash check, it is chucked out immediately and re-downloaded from somewhere else.

Thanks, that's nice to know.  So many times I've had to re-download something because it was corrupted in the process.  At least this has a better chance of not being corrupt.
Wait until you see my next posts.  My connection is really slow at the moment because BT is doing it's thing as I type.

---

### Post by Bruce M. on 2007-11-11
Well, here I am again.  Couldn't do anything last night.  My wife wanted the computer.  And we share.  :)

But I am downloading a torrent now from one of the sites that was posted here earlier.
I'm getting a movie (that I really don't want) as a test.  But some questions as to what's happening.

Screeshot.png is 2 miniutes into the download, and if I read it right the sharing rate is not good. 0 in fact as you can see in screenshot-1.png

  EDIT:  Can't add screenshots, they are too big.  Hope I can get som answers anyway.    :(
Where can I put them if you need/want to see them?  (OK, that's a question too)

Questions: ( C-x = Column-Number )

Q 1. What are all those IP's where there is NO action? (C-2 & C-3)

Q 2. C-1: Op [Optimistic Unchoke]  - What is this?

      Then comes C-2 [Peer ID]  & C-3 [IP] - these I understand.

Q 3. C-4: [Local/Remote]  Whose local or remote?

     C-5 - understood.

Q 4. C-6 [Interested] and C-7 [Choking] - What are these?

     C-8 [Down] - hmmm the opposite of Up?  :lolflag:  -loading-

Q 5. C-9 [Choked] & C-10 [Snubbed] - Again, what are these?

   The rest are self explanatory for ... well, for me anyway.       :lolflag:

---

### Post by Bruce M. on 2007-11-11
I've been at this for 2hrs 20min - says I have another 12 hours 02 minutes to go!

When I started it said: 13 hours. 43 minutes

Download rate is dancing between 7-8 k/B sec
With HTTP I average 12-14 k/B sec

This is NOT good.    :(

---

### Post by P4man on 2007-11-11
both speeds are horrible. Are you on a 56k modem ?
Also, tell me which torrent, I can try and see what speed I get out of it. Or better, try the ubuntu torrent, that will ensure the torrent is not the problem.

---

### Post by wog on 2007-11-11
Routers are your friends, provided you have the room for a second computer. :)
If you don't have the cash or space for an entire computer, there are some reasonably good KVM switches out there for cheap. Check newegg.com and look in the less-than $50 bracket.

Yes, sometimes download speeds are slow, but they fluctuate over time. For myself, I notice I get the best speeds around midnight to five am, when I'm comfortably asleep. And good speeds in this case are hovering around 100 to 200 kb/s.

I'm not really sure about the no-activity IPs. I assume they're either downloading from someone else at the time, or they're suffering from Comcast's latest stupidity regarding bias against p2p software like BT.

For some of these terms you might check the BT website. Google for it and you should find it pretty easily. It should be something like bittorrent.com.

---

### Post by Bruce M. on 2007-11-11
Hi P4man,

> **P4man said:**
> both speeds are horrible. Are you on a 56k modem ?
Also, tell me which torrent, I can try and see what speed I get out of it. Or better, try the ubuntu torrent, that will ensure the torrent is not the problem.

Yea, they are horrible.  I'm on a cable-modem.  My connect speed is 100 Mb/s   :(

When I started the download BitTorrent popped up.  Guess that's my default.
I also have:  Azureus and Bittornado

---

### Post by Bruce M. on 2007-11-11
> **wog said:**
> Routers are your friends, provided you have the room for a second computer. :)
If you don't have the cash or space for an entire computer, there are some reasonably good KVM switches out there for cheap. Check newegg.com and look in the less-than $50 bracket.

"Second computer, second computer he says!.  HAHAHAHAHA"  (that's my wallet laughing).  I was going into panic mode when the old OS crashed and I thought I'd have to buy a new computer to support the upgrade to a new version of that other OS.  Ubuntu breathed life into this old PC.  Just so you know, my wife and I live on my small pension.   :)

Newegg.com is in the US isn't it?  It would cost me more for shipping than the cost of the switch I think. (what ever that is - I'll google it.)

> **wog said:**
> Yes, sometimes download speeds are slow, but they fluctuate over time. For myself, I notice I get the best speeds around midnight to five am, when I'm comfortably asleep. And good speeds in this case are hovering around 100 to 200 kb/s.

How lucky, I've **never** seen speeds like that.

> **wog said:**
> I'm not really sure about the no-activity IPs. I assume they're either downloading from someone else at the time, or they're suffering from Comcast's latest stupidity regarding bias against p2p software like BT.

I figured as much, but didn't want to "assume".  I did check a site ( Azureus ) that has a "Bad ISP" page, and my ISP was not listed, although the other 3 large ISP's here were.

> **wog said:**
> For some of these terms you might check the BT website. Google for it and you should find it pretty easily. It should be something like bittorrent.com.

Hmmmm, I have it bookmarked already, and had a look around a few days ago.  Guess I'll head back and do more looking.  Thanks wog, good hearing from you.

---

### Post by bgast1 on 2007-11-11
Somewhere, I think in this thread it was suggested that we seed for a 1/1 ratio. Where do we see this ratio at? I am using Deluge.

---

### Post by dfreer on 2007-11-11
@bgast - It depends on your bittorrent client where that information (if it is even available) is located, I don't use deluge myself.

@Bruce M. - Bittorrent can be tricky at times. You may be downloading a .torrent that doesn't have many peers/seeds, or your router may be blocking the incoming connections from peers, or it may be an ISP related issue. Since there are several variables involved, I suggest that you try downloading the Ubuntu 7.10 i386 LiveCD before you try others, the Gutsy CD has plenty of peers/seeds for sure ;)
Due to the nature of bittorrent technology, downloads always start slow, and slow pick up speed as you connect to more and more peers, discarding slower peers in favor of faster ones. For that reason, you shouldn't rely on speed readings within the first, oh say 5-10 minutes of starting the download. Also, every time you stop your download, you'll need to wait yet again when resuming.

RE: the Cable Modem connected at 100Mb/s (FYI). If that were really the case you'd probably would've seen speeds MUCH higher than 100-200Kb/s. More likely, you have a 100Mb/s connection between your PC and your Cable Modem/Router, which would then have a seperate speed between it and the ISP itself (Your ISP will likely measure your connection in bits, not bytes like any sane computer person would ;p ). You can run a speed test here:
[http://www.dslreports.com/stest](http://www.dslreports.com/stest)
To get some idea of your connection to your ISP.

EDIT: Couldn't find the link to the bittorrent downloads on ubuntu's site, but I know that by choosing a mirror, and then instead of downloading the .ISO, you can cut out the last part of the download URL like so:
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso)
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/)
And therein you will find the official .torrents for all the versions, like this one I linked for you:
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso.torrent](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso.torrent)

---

### Post by mivo on 2007-11-11
> **bgast1 said:**
> Somewhere, I think in this thread it was suggested that we seed for a 1/1 ratio. Where do we see this ratio at? I am using Deluge.

In the "details" tab of a file, there is an entry called "share ratio" (left column).

---

### Post by Bruce M. on 2007-11-12
> **dfreer said:**
> @Bruce M. - Bittorrent can be tricky at times. You may be downloading a .torrent that doesn't have many peers/seeds, or your router may be blocking the incoming connections from peers, or it may be an ISP related issue. Since there are several variables involved, I suggest that you try downloading the Ubuntu 7.10 i386 LiveCD before you try others, the Gutsy CD has plenty of peers/seeds for sure ;)
Due to the nature of bittorrent technology, downloads always start slow, and slow pick up speed as you connect to more and more peers, discarding slower peers in favor of faster ones. For that reason, you shouldn't rely on speed readings within the first, oh say 5-10 minutes of starting the download. Also, every time you stop your download, you'll need to wait yet again when resuming.

From the "screencapture PNG's I have at the 2 hour mark, there were at least 8 connections and I was clocked in @ 12 kB/sec..

Lets try something, an HTTP download of Gutsy ... 
Download URL: [http://mirror.pop-sc.rnp.br/mirror/ubuntu/gutsy/ubuntu-7.10-desktop-i386.iso](http://mirror.pop-sc.rnp.br/mirror/ubuntu/gutsy/ubuntu-7.10-desktop-i386.iso)
Ubuntu Edition: Ubuntu 7.10 desktop
Computer Platform: i386
Download Location: [http://mirror.pop-sc.rnp.br/mirror/ubuntu/](http://mirror.pop-sc.rnp.br/mirror/ubuntu/)

0.0 of 695.8MB @ 16KB/sec - didn't get the time left.
5.0 of 695.8MB @ 15.3 KB/sec - 12h 51m left
6.0 of 695.8MB @ 15.3 KB/sec - 12h 50m left
Removed the download at this point.

Is there a difference between K & k as in: KB/sec and kB/sec or Kbps - kbps?

b = bits  B = Bytes (8bits)  if my memory serves me correct.

> **dfreer said:**
> RE: the Cable Modem connected at 100Mb/s (FYI). If that were really the case you'd probably would've seen speeds MUCH higher than 100-200Kb/s. More likely, you have a 100Mb/s connection between your PC and your Cable Modem/Router, which would then have a seperate speed between it and the ISP itself (Your ISP will likely measure your connection in bits, not bytes like any sane computer person would ;p ). You can run a speed test here:
[http://www.dslreports.com/stest](http://www.dslreports.com/stest)
To get some idea of your connection to your ISP.

Take a look at these images from 4 tests I did.
For example 123 Kbps Kilo-bits/sec = 123/8 = 15.3 KB/s - that looks like what I get.

> **dfreer said:**
> EDIT: Couldn't find the link to the bittorrent downloads on ubuntu's site, but I know that by choosing a mirror, and then instead of downloading the .ISO, you can cut out the last part of the download URL like so:
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso)
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/)
And therein you will find the official .torrents for all the versions, like this one I linked for you:
[http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso.torrent](http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso.torrent)

I'll keep that for when I'm ready to get Gutsy   :)  Thanks.
I'm a little surprised they don't have links to the torrents.

---

### Post by Bruce M. on 2007-11-12
Thought I'd add this as well...

A test from a site in Argentina found the link at [http://speedtest.dslreports.com](http://speedtest.dslreports.com) that you gave me dfreer.

Fecha: Mon, 12 Nov 2007 17:39:58 GMT
Pruebas de Descarga:
Informar al Operador la velocidad aproximada:
Primera 128K tomo 9092 ms = 14416 Bytes/sec = Velocidad aproximada: 115 Kbps 
Segunda 128K tomo 8540 ms = 15348 Bytes/sec = Velocidad aproximada: 123 Kbps 
Tercera 128K tomo 8531 ms = 15364 Bytes/sec = Velocidad aproximada: 123 Kbps 
Cuarta  128K tomo 8518 ms = 15388 Bytes/sec = Velocidad aproximada: 123 Kbps

Looks the same.

---

### Post by wog on 2007-11-12
Wow. 

This is the result I got for [http://speedtest.dslreports.com]("http://speedtest.dslreports.com")

[IMG]http://www.dslreports.com/im/39731955/34541.png[/IMG]

---

### Post by P4man on 2007-11-12
There is something terribly wrong with your connection or ISP. Those speeds are totally appalling.
I get 400+KByte /s  (3200 Kbit) from the official ubuntu torrents here:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

and I dont even have a particularly good ISP or connection.

What ISP and what program (I mean "plan" or "scheme" or whatever they call it)  do you have ? I certainly hope you are not paying broadband prices, because you have smallband speed.

**Edit:** a local testsite gave me this

down
Your DOWNLOAD Speed:
3006 kbps or 376 KB/sec

up
Your UPLOAD Speed:
316 kbps or 40 KB/sec 

Which is about what you would expect from the 4Mbit ADSL connection that I have.

---

### Post by Bruce M. on 2007-11-12
> **wog said:**
> Wow. 

This is the result I got for [http://speedtest.dslreports.com]("http://speedtest.dslreports.com")

[IMG]http://www.dslreports.com/im/39731955/34541.png[/IMG]

wog ... I only have one thing to say to you:

 :( :( :( :( :( :(  - Do you know what you've done!!!!

Now I've deluted my coffee with salty tears!

You must get a new release ISO file in like what - 30 minutes?

GRRRRRRRRRRRRRRRRR!!!!!!!!!!!!!!!!!!           :)

---

### Post by wog on 2007-11-12
> **Bruce M. said:**
> 

You must get a new release ISO file in like what - 30 minutes?



Somewhere between that and a couple of hours. Sometimes BT slows down.

Lately Comcast (whom I have my connection through) has been making news by biasing their connections against BT. I really want to help alleviate strain on people's servers by using BT, but sometimes it's just faster to use HTTP.

The other issue which slows a Cable connection is the full signal is sort of shared between all the people in the neighborhood who also have cable broadband. Well, I live out in the sticks, so there's almost no-one else near me who uses broadband. 

So that's what gives me this outrageous speed.

Honestly, at the speeds you're getting, if you have cable there must be a lot of people around you also using broadband. To get full speed, you'd have to switch to DSL, where you're guaranteed a certain rate of speed, though you pay by the gigabyte for throughput.

I don't know yet what else I could suggest.

---

### Post by Bruce M. on 2007-11-12
> **P4man said:**
> There is something terribly wrong with your connection or ISP. Those speeds are totally appalling.
I get 400+KByte /s  (3200 Kbit) from the official ubuntu torrents here:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

and I dont even have a particularly good ISP or connection.

What ISP and what program (I mean "plan" or "scheme" or whatever they call it)  do you have ? I certainly hope you are not paying broadband prices, because you have smallband speed.

OK.  [COLOR="Red"]**Think:**[/COLOR]  **Windows mindset vs Linux mindset**
I live in Argentina, so switch Windows for Argentina and Linux for USA
To get **Argentina mindset vs USA mindset**
Now that we're running on parallel tracks read on.

Our plan is:  FLASH B.ANCHA CM128K ... a bit more than double my USR 56K modem.
{B.ANCHA = Banda Ancha = Wide Band} and we're paying for 128K - 24/7

It's the cheapest they have here at $49.90 pesos a month ( U$ 15.96 )

And here **_every_** time you use the phone you pay for it.  So having a modem here is not really cost effective.  By switching to this cable-modem plan we saved over $60 pesos a month on our phone bill. 

> **P4man said:**
> **Edit:** a local testsite gave me this

down
Your DOWNLOAD Speed:
3006 kbps or 376 KB/sec

up
Your UPLOAD Speed:
316 kbps or 40 KB/sec 

Which is about what you would expect from the 4Mbit ADSL connection that I have.

But 4Mbits is a lot more then 128K, if you want to cry in your beer look at wog's test above.

---

### Post by anemptygun on 2007-11-12
It's funny how most people have this first impression.. I know I did. Bittorrent is evil argh! But now I am a changed man!

---

### Post by Bruce M. on 2007-11-12
> **wog said:**
> Somewhere between that and a couple of hours. Sometimes BT slows down.

Lately Comcast (whom I have my connection through) has been making news by biasing their connections against BT. I really want to help alleviate strain on people's servers by using BT, but sometimes it's just faster to use HTTP.

The other issue which slows a Cable connection is the full signal is sort of shared between all the people in the neighborhood who also have cable broadband. Well, I live out in the sticks, so there's almost no-one else near me who uses broadband. 

So that's what gives me this outrageous speed.

You're one lucky SOB {buddy ... I meant: **Buddy**!}   :)

Greater Buenos Aires - approx 16 million people.  Yup, I'd bet a ***_[COLOR="Red"]FEW[/COLOR]_*** of them are using cable-modems like me.   :lolflag:

> **wog said:**
> Honestly, at the speeds you're getting, if you have cable there must be a lot of people around you also using broadband. To get full speed, you'd have to switch to DSL, where you're guaranteed a certain rate of speed, though you pay by the gigabyte for throughput.

To quote myself:

> 
OK. Think: **Windows mindset vs Linux mindset**
I live in Argentina, so switch Windows for Argentina and Linux for USA
To get **Argentina mindset vs USA mindset**
Now that we're running on parallel tracks read on.

Our plan is: FLASH B.ANCHA CM128K ... a bit more than double my USR 56K modem.
{B.ANCHA = Banda Ancha = Wide Band} and we're paying for 128K - 24/7

It's the cheapest they have here at $49.90 pesos a month ( U$ 15.96 )

And here every time you use the phone you pay for it. So having a modem here is not really cost effective. By switching to this cable-modem plan we saved over $60 pesos a month on our phone bill.

and add a comment:  **This encludes using DSL.**       :(

> **wog said:**
> I don't know yet what else I could suggest.

That's OK, I'll just go get my 31st coffee for the day.....    :(
And prepare for an overnight "upgrade" session but that means I won't have a CD backup.

OH I know what you can do. Why not take a winter vacation in January {packing light summer cloths] and come to BsAs for a holiday.

Oh, and before you come, can you download Gutsy Gibbon Alternate CD (i386) for me.   :lolflag:

---

### Post by Bruce M. on 2007-11-12
> **anemptygun said:**
> It's funny how most people have this first impression.. I know I did. Bittorrent is evil argh! But now I am a changed man!

Yup, me too!

---

### Post by wog on 2007-11-12
Oh, THAT'S the problem. I see your solution now.

On the Ubuntu website there's a place where they will send you a copy of the install discs.
Here: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Tell them your address and then wait for it to arrive. Presto! You'll have a working copy of the install discs. Problem solved?

---

### Post by dfreer on 2007-11-12
**@Bruce M.** - 
> Is there a difference between K & k as in: KB/sec and kB/sec or Kbps - kbps?
b = bits B = Bytes (8bits) if my memory serves me correct.

Sounds right to me.

IANAE, but based on your connection, I don't know whether bittorrent will really be of much use to you. With your connection (which sounds like 128Kbps), you'll probably be downloading files at your max capactity using standard HTTP because you'll be hardly putting a strain on the server's upload capacity. Using HTTP, the download will start immediately whereas the .torrent will take a while to connect to the tracker and connect to peers, so in some cases HTTP may indeed be quicker for you. 

This is the part where I myself would perform several tests. But I'm crazy like that ;)

That being said, the other advantages of bittorrent can still apply (hash of individual pieces of the .torrent, so that if a part of a file gets corrupted it will automatically discard it without having to restart the entire download, pausing/resuming, etc). 

**@Anyone using dslreports.com for speed tests** - As it says, for an accurate picture of your connection speeds you need to make sure no one is using your connection. As cable modem users tend to share bandwidth with other customer's in their area, you will most likely want to run a series of tests, repeating each multiple times to really get an accurate picture. 

I generally run the test 2-3 times, one after another, throwing out any extreme results, and then repeat it during different times during the day (I'd imagine, peak hours sometimes between the hours of 5-10 PM on weekdays, possibly 6-9 AM as well? I only had a cable modem for about half a year during high school myself). 

ISP's as said like to list their connections in terms of bits, whereas almost all software on PC's will report speeds in terms of bytes (firefox, wget, you know what I mean). dslreports.com will report it's results in bits, although using the Java plugin and selecting "Result as Text", I got both results in bits and bytes. 

I'll post my results on my 3 Mbps fiber optic connection (dunno why fiber is that low, I know I can upgrade to 5 Mbps but shouldn't fiber be capable of so much more?) when it's not in use later tonight.

EDIT: Also, you would only share your cable with a selection of your neighbors, not your entire city I'd imagine.

---

### Post by Bruce M. on 2007-11-12
> **wog said:**
> Oh, THAT'S the problem. I see your solution now.

Hahahahaha, didn't like the idea of a summer vacation in January huh!  But why not?

Did the plane fare + hotel cost + food bill = **A LOT more then U$1.00** versus the cost of a FREE OS + U$1.00 for the CD = **U$1.00** not equal out in your books?

[CENTER]:lolflag:[/CENTER]

> **wog said:**
> On the Ubuntu website there's a place where they will send you a copy of the install discs.
Here: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Tell them your address and then wait for it to arrive. Presto! You'll have a working copy of the install discs. Problem solved?

I already did that with Feisty Fawn, I have the original "Live CD" and spent a night getting the Alternate CD.

And trust me, I have no problems doing it again ( 2 nights ) one for live "upgrading" and the second to get the Alternate CD ISO file.

In fact I'll probably do it three times: to get a 7.10 Live CD too.  So I can show/give it to friends.

I was just hoping that BT (I've changed my mind about it) could shorten the 12-14 hour download a bit.
[B]
Originally I got 6.04 at a CyberCafe (took 2 hours) (they have a 1GIG connection - but 24 other machines were playing games on the net)[/B]

There are my two new CD's, I'll do that again.  The answer was staring me in the face all this time.  :)

---

### Post by Bruce M. on 2007-11-12
Hi dfreer

> **dfreer said:**
> **@Bruce M.** - 

Sounds right to me.

IANAE

Acronym	Definition
IANAE	I Am Not An Economist
IANAE	I Am Not An Expert (often used in newsgroups)

See, learn something every day.

> **dfreer said:**
> but based on your connection, I don't know whether bittorrent will really be of much use to you. With your connection (which sounds like 128Kbps), you'll probably be downloading files at your max capactity using standard HTTP because you'll be hardly putting a strain on the server's upload capacity. Using HTTP, the download will start immediately whereas the .torrent will take a while to connect to the tracker and connect to peers, so in some cases HTTP may indeed be quicker for you.

This is the part where I myself would perform several tests. But I'm crazy like that ;)

I'm coming to the same conclusion.  Since I getting 1Meg +/- a minute with HTTP and less or equal with BT.
But I'll have to try ONCE for a complete BT download (Ubuntu Gutsy) to see what the *end* results are.


> **dfreer said:**
> That being said, the other advantages of bittorrent can still apply (hash of individual pieces of the .torrent, so that if a part of a file gets corrupted it will automatically discard it without having to restart the entire download, pausing/resuming, etc).

This is why I want to try one test (GG) I already had a bad download that took overnight.

> **dfreer said:**
> [B]EDIT: Also, you would only share your cable with a selection of your neighbors, not your entire city I'd imagine.

Oh I'm sure that's true.  The selection of my neighbours probably only encludes, 20+ thousand minus, cable-modems from the other company, the DSL people, the regular modems .... probably down to a few thousand by now.

Who knows ....  I'm happy.    :-\"

---

### Post by P4man on 2007-11-12
Bittorrent can not alliviate  a slow connection. No protocol can. The best you can hope for is getting "line speed", so the maximum speed your connection allows. Your line speed is pretty low, so in most cases HTTP, FTP or bittorrent won't make a tangible speed difference for you. Bittorrent might even end up a bit slower because of the protocol overhead.

Its only us "lucky bastards" (compared to you) with multiple megabit connections that are often slowed down by the servers, so we complain when we only get like 100Kbyte/s. Bittorrent can help us getting close to line speed again, especially compared to overloaded HTTP servers.

Anyway, bittorrent should still be very interesting for you, not for the speed, but because of the ability to resume downloads, and the greater certainty you do not end up with a corrupt file. If that happens to one of us, no problemo, we just download it again. But if you had to wait 2 days and then end up with a corrupt file, that must hurt!

One more thing: I read another thread here from someone from India IIRC, that didn't have an internet connection to his PC. He downloaded the Ubuntu iso via his mobile phone, on EDGE!! that is what, around 50kbit/s ? So forget about us, and consider yourself lucky :p

Here is the thread if you are interested:
[http://ubuntuforums.org/showthread.php?t=609678&page=2](http://ubuntuforums.org/showthread.php?t=609678&page=2)

---

### Post by mivo on 2007-11-12
> **wog said:**
> On the Ubuntu website there's a place where they will send you a copy of the install discs. Here: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

And they even include several Ubuntu stickers, too!  Downside is that it will probably take several weeks to get the disks.

---

### Post by inversekinetix on 2007-11-12
I love bittorrent.  for windows uTorrent (anything before 1.6.1)

for ubunty Ktorrent.

The speeds I get on well seeded torrents are obscene!

I managed to get 60MB/s          from a server in tokyo  
I've managed to upload at 27MB/s on 3 well leeched torrents connecting to 800 peers.

It blows my mind.

---

### Post by dfreer on 2007-11-12
Must be nice to have fiber at 1Gbps holy frick! If you don't mind, do you live in the US? what city/state has that kind of speeds available to home consumers?!

---

### Post by wog on 2007-11-13
> **Bruce M. said:**
> Hahahahaha, didn't like the idea of a summer vacation in January huh!  But why not?

Did the plane fare + hotel cost + food bill = **A LOT more then U$1.00** versus the cost of a FREE OS + U$1.00 for the CD = **U$1.00** not equal out in your books?

Oh, no, that's not the problem. The problem is even before I could think about the air fare and hotel cost and food bills, there'd be the matter of my wife finding enough time off to make the trip, and convincing her to want to make the trip out there.

But if I was going all that way, I'd also bring my laptop, a wireless router for you to keep when we left, and both CDs of Ubuntu. There'd be no point in visiting you empty handed. :)

The pity'd be I don't have a spare machine I could leave there so you could always have one machine constantly downloading while your wife uses her machine when she wants to. Trust me, I understand how it goes when you share the computer. Having the extra one with a router so you share the connection is the very best, no matter what the speed you're limited to. :)

regards,
James

---

### Post by Bruce M. on 2007-11-13
Hi dfreer

> **dfreer said:**
> Must be nice to have fiber at 1Gbps holy frick! If you don't mind, do you live in the US? what city/state has that kind of speeds available to home consumers?!

Are you pointing this at me?

> Originally I got 6.04 at a [COLOR="Red"]**CyberCafe**[/COLOR] (took 2 hours) (they have a 1GIG connection - but 24 other machines were playing games on the net)

Not 1Gig at home, a CyberCafe.  Set up with 25 machines where people play games on line.

Do I live in the US - no - Buenos Aires, Argentina.
As to your next question - I have no idea ( No tengo ni idea )  :lolflag:

---

### Post by Bruce M. on 2007-11-13
> **P4man said:**
> Bittorrent can not alleviate  a slow connection. No protocol can. The best you can hope for is getting "line speed", so the maximum speed your connection allows. Your line speed is pretty low, so in most cases HTTP, FTP or bittorrent won't make a tangible speed difference for you. Bittorrent might even end up a bit slower because of the protocol overhead.

Its only us "lucky bastards" (compared to you) with multiple megabit connections that are often slowed down by the servers, so we complain when we only get like 100Kbyte/s. Bittorrent can help us getting close to line speed again, especially compared to overloaded HTTP servers.

I realize that now ... see below.

> **P4man said:**
> Anyway, bittorrent should still be very interesting for you, not for the speed, but because of the ability to resume downloads, and the greater certainty you do not end up with a corrupt file. If that happens to one of us, no problemo, we just download it again. But if you had to wait 2 days and then end up with a corrupt file, that must hurt!

Yes, it does, but it was 14 hours not 2 days, but since the connect is 24/7 without extra charges, it's not a problem.  At least I slept through a portion of that.  :)  I could never have afforded it with my USR 56K modem because of the extra phone charges.

> **P4man said:**
> One more thing: I read another thread here from someone from India IIRC, that didn't have an internet connection to his PC. He downloaded the Ubuntu iso via his mobile phone, on EDGE!! that is what, around 50kbit/s ? So forget about us, and consider yourself lucky :p

Here is the thread if you are interested:
[http://ubuntuforums.org/showthread.php?t=609678&page=2](http://ubuntuforums.org/showthread.php?t=609678&page=2)

WoW!  Now that's something.  Don't have time to read it at the moment but I will later today.

---

### Post by Bruce M. on 2007-11-13
Hi James

> **wog said:**
> Oh, no, that's not the problem. The problem is even before I could think about the air fare and hotel cost and food bills, there'd be the matter of my wife finding enough time off to make the trip, and convincing her to want to make the trip out there.

I was just kidding when I wrote that about coming here.  I never in my wildest thoughts would I have thought you'd even consider it.

> **wog said:**
> But if I was going all that way, I'd also bring my laptop, a wireless router for you to keep when we left, and both CDs of Ubuntu. There'd be no point in visiting you empty handed. :)

I had to look up "wireless router" to see what it is:

> The WRT54G is also quite notable for being a piece of networking equipment that even novice home computer users understand and use each day. The WRT54G can be thought of as bridging the gap between high-end commercial networking and the now-booming home networking.

Well no wonder I had no idea, I've never in my life owned more than one machine at a time.  So home networking never entered the equation Never needed more then one.
But I certainly would not have said no to the disks.   

> **wog said:**
> The pity'd be I don't have a spare machine I could leave there so you could always have one machine constantly downloading while your wife uses her machine when she wants to. Trust me, I understand how it goes when you share the computer. Having the extra one with a router so you share the connection is the very best, no matter what the speed you're limited to. :)

regards,
James

You're to kind for even saying that.  But it would really be a waste.  First off, there is just no room for a second machine, and it would basically just collect dust anyway.  We have no problem sharing this computer, neither of us uses the computer for work so it's not a big issue.  Just collecting email, a bit of cruising the web, online banking.

I'm not a programmer, don't listen to music on the computer (90% of the time the speakers are off), don't watch movies, TV or listen to the radio.  We have a DVD player and a stereo for that. Games?  Shhh don't tell anyone but we have a PS2.  I don't do graphics, although I'm struggling with trying to do one specific thing in Gimp, and if I get frustrated enough I'll ask the question, but have to try myself first.

Have a GREAT day, CHIMO!
Bruce

---

### Post by dfreer on 2007-11-13
> **dfreer said:**
> [QUOTE=inversekinetix;3760678]
I managed to get **60MB/s**          from a server in tokyo  
I've managed to upload at **27MB/s** on 3 well leeched torrents connecting to 800 peers.

q6660 2.4GHz(o/c 3GHz)(8MB L2), Asus P5K, 4GB DDR2(5-5-515), pk8800GTS TDH 640MB, 1x 500GB IDE, 3x500GB SATA II, 1x80GB IDE, Antec p180, **1Gb fibre**  xp pro - gutsy 

Must be nice to have fiber at 1Gbps holy frick! If you don't mind, do you live in the US? what city/state has that kind of speeds available to home consumers?![/QUOTE]

Also, Finally got around to running a speed test here:
```
Speed Test #39789415 by dslreports.com
Run: 2007-11-13 10:57:56 EST
Download: 2395 (Kbps)
Upload: 1002 (Kbps)
In kilobytes per second: 292.4 down 122.3 up
Tested by server: 56 java

```

Not quite as fast as it should be (I should be getting ~3 Mb/s), but it's understandable.

---

### Post by Bruce M. on 2007-11-13
> **mivo said:**
> And they even include several Ubuntu stickers, too!  Downside is that it will probably take several weeks to get the disks.

I got my first CD (Feisty) in less then two weeks.  I consider myself lucky.   :)

---

### Post by Bruce M. on 2007-11-13
Hi folks,

My original idea was to get advantages and disadvantages of using "bittorrents" or BT.

Well from reading what has been posted here I get the following.

Most are direct quotes, some have been edited by me.  No names, no backpack, no drill, just the meat of what this about.

If you can add something to either Advantages or Disadvantages please let me know, and don't forget the Extra Info I added because I thought it pertinent while not necessarily an advantage or disadvantage.


--------------
ADVANTAGES:

1. Lots of people downloading via Bittorrent -> Fast download speeds
   Lots of people downloading via HTTP -> Slow download speeds

2. Can pause a download and resume it later. Also disconnections don't cause any real problems.  My connection is relatively slow (DSL with 384kbit, so 45k/s), so the ability to pause and resume downloads is important.
	NOTE: On BT (the default torrent program in Ubuntu), to resume a file after breaking off at some point, open the torrent file you used to start your download in the first place. When BT asks where to save the file, point it at the same directory you downloaded to before. BT detects the file automatically, checks to see how much of the file is actually there, and resumes.

3. Generally, popular torrents will pretty much max out your connection speed, which is more than can be said about most HTTP download sites.

4.  Most bittorrent clients allow you to select which files in any given torrent you actually want to download. Let's say there was a mega-collection of all of the Ubuntu variants (Ubuntu, Kbuntu, Xbuntu, etc). But you only want to download Kbuntu and Ubuntu, and none of the others. You can download the .torrent associated for the entire collection, and just select those two. The download will proceed, and you can even seed just those two files if you wish (although most tracker will still list you as leeching instead of seeding, because you don't have the entire collection. This will not be a problem in most cases). In the future, you can even go back and download ones you missed without any issues.

5. Another benefit of using torrents is that the hash of each piece of the torrent is checked as you download it, so you are more likely to get an uncorrupted file than by regular HTTP downloading. If a piece fails the hash check, it is chucked out immediately and re-downloaded from somewhere else.


--------------
DISADVANTAGES:

1. Few people downloading via Bittorrent -> Slow download speeds
   Few people downloading via HTTP - > Fast download speeds

2. The main problem with bittorrent right now, is that unpopular files or files that no one needs can become extremely difficult, if not impossible to download. For example, I once tried downloading "a completely legal copy of something incredibly boring ", got 80% of the download completed only to realize that out of the 4 peers that I was downloading with, none of us had the complete file. So we all ended up stuck at 80% waiting for someone to come along with a complete copy (a seeder), eventually I gave up.

2. Some ISPs deliberately slow down bittorrent traffic (and similar peer2peer protocols).  Check your ISP!


--------------
Extra Info:

	The idea behind BT is that rather than having a single point from which everyone downloads (rapidly causing congestion at that point) is that everyone downloading, also uploads to other downloaders at the same time. This spreads the bandwidth requirements which makes a lot of sense.
	Consider Ubuntu. When a new version is released, and tens of thousands of people want to download that 750 Mb ISO file it causes massive problems for Canonical (and its mirrors). With BT, I can seed Ubuntu from my home network, and everyone can download it at the same speed as a single user. The more users downloading it, the more bandwidth the entire group ("swarm" in BT terms) gets.

------------
	Bittorrent can not alleviate a slow connection. No protocol can. The best you can hope for is getting "line speed", so the maximum speed your connection allows. Your line speed is pretty low, so in most cases HTTP, FTP or bittorrent won't make a tangible speed difference for you. Bittorrent might even end up a bit slower because of the protocol overhead.

------------
	STATEMENT: Others using my bandwidth. {Don't close Bit Torrent, keep the connection alive as long as possible}

	EXPLANATION: You are using other people's bandwidth when you download, its is expected you give back as well. To be fair, you should aim for a share ratio of around 1/1. Meaning, you upload as much as you downloaded. Most connections will download much faster than upload, so when you have downloaded your 750Mb file, you might only have uploaded 75Mb. For BT networks to keep working, people should keep their BT client open to seed (upload) until they have reached that ratio. So yes, in total you will have used 1.5GB traffic to download 750Mb. If your ISP doesn't put too severe caps on your bandwidth it shouldn't be a problem. And if your ISP does that, no one is going to kill you if you do stop uploading

	MORE SIMPLY PUT:  When you're using BT you'll get a higher level of activity. BT is making your copy of the file available for others to download, just as others are sharing their copy for you to get it from them.

------------
	Bittorrent is great, I like to think of it as a "counterpart" or inverse of the standard HTTP download:

Lots of people downloading via HTTP -> Slow download speeds
Few people downloading via HTTP - > Fast download speeds
Lots of people downloading via Bittorrent -> Fast download speeds
Few people downloading via Bittorrent -> Slow download speeds

---

### Post by inversekinetix on 2007-11-14
> **dfreer said:**
> Must be nice to have fiber at 1Gbps holy frick! If you don't mind, do you live in the US? what city/state has that kind of speeds available to home consumers?!

I live in japan.  I was the first to get fiber in my area and now theres only one other person using it.  I was using BT about a month ago, downloading 20 or so torrents with 1000s of connected peers and all of a sudden there was a loud bang and my router stopped working.  Arrg, internet gone. A tech came by and replaced the router, fibre box and ipphone modem, he noticed I had mame on so we spent an hour playing that.  

I asked him to uncap my line (in terms of transfer rate/theres no traffic limit) , apparently its not capped at all and cant be made faster :(

best part is I only pay $40 a month for it

---

