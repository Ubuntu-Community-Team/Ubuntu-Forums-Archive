---
title: "good torrent program"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by mbt12 on 2007-08-21
I have no idea how to use torrents, but I think I am going to try.  What is a good torrent program I can use and also is there a site with a walkthrough? thanks

---

### Post by Hobo Joe on 2007-08-21
Azureus is the best in my opinion.

---

### Post by wolfen69 on 2007-08-21
ktorrent and bittornado are good.

---

### Post by Dr Small on 2007-08-21
Applications > Internet > BitTorrent might help?

---

### Post by mbt12 on 2007-08-21
> **Dr Small said:**
> Applications > Internet > BitTorrent might help?

BitTorrent is not on that list

---

### Post by Hobo Joe on 2007-08-21
```

sudo aptitude install azureus

```

---

### Post by CapitanYochua on 2007-08-21
Deluge. Is good. Pretty new, but with potential.

---

### Post by mbt12 on 2007-08-21
While I was testing the TCP listening port it said NAT error.  How do I fix this?  btw, I installed azureus

---

### Post by alican timur on 2007-08-21
I'm using deluge, and even though i have a download/upload limit that is 110/90 kb/sec, i'm accused of leeching!

i get the error in the tracker status display : access denied, leeching forbidden, you are only allowed to seed (http code = 200, times in a row=11)

why do i get that?

---

### Post by funrider on 2007-08-21
i tried azerus, gtorrent and some other problem but i like ktorrent the most! it is customizable and you change the memory allocated to it.

---

### Post by mbt12 on 2007-08-21
anyone know about that NAT error?

---

### Post by Acglaphotis on 2007-08-21
KTORRENT FTW

/end Fanboyism

Or you could try uTorrent with wine. Works awesome.

---

### Post by Aishiko on 2007-08-21
I've used under windows Averus, basic BitTorrent, TorandoTorrent, and a couple others Averus was a memory leaking pain, I ended up staying with TorandoTorrent I'm not sure what I'm going to use under Linux.

---

### Post by mbt12 on 2007-08-21
How do I download that and would that fix the NAT error?

---

### Post by Frak on 2007-08-21
Azureus, gtorrent, Deluge, and uTorrent (under Wine)

---

### Post by celloandy on 2007-08-25
> **mbt12 said:**
> anyone know about that NAT error?
You're getting this error because you're using some sort of a router, and the router is preventing other torrent clients from directly connecting your machine.  To make it work, check in the preferences to see what TCP port is being used for your torrents (you can actually change it if you want, and it might be a good idea to do so, since lots of ISPs monitor and throttle traffic on the standard ports... if you change it, just choose a big number: 50000+).

Figure out what the IP address of your computer is (right-click on the Network Manager icon in the notification area click "Connection Information" to find out), then log into your router's configuration menu and configure the router to forward the requisite TCP port to your IP (consult your router's manual, as the procedure will vary).  Note that if your computer gets its IP dynamically via DHCP, your IP address may change from time to time, and you may need to update your forward accordingly.  If you torrent heavily, it may be worth setting up a static IP for your machine or, if your router supports it, configuring its DHCP to assign specific IPs to certain MAC addresses.

Some torrent clients (I think Azureus, maybe?) support UPnP NAT Traversal, which should be able to auto-negotiate ports without you having to do anything, if your router supports it.  I've always had better luck with the manual forwards, though.

Best of luck.

Andrew

---

### Post by hyper_ch on 2007-08-25
rTorrent - command line based and very light but powerful.

---

### Post by Golyadkin on 2007-08-25
My vote is for Deluge, definitely. Just download and doubleclick this file to install: [http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.4.1/&file=deluge-torrent_0.5.4.1-1_i386.deb](http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.4.1/&file=deluge-torrent_0.5.4.1-1_i386.deb)

---

### Post by mali2297 on 2007-08-25
> **hyper_ch said:**
> rTorrent - command line based and very light but powerful.

I second this. For walkthroughs, look here:

[http://libtorrent.rakshasa.no/]("http://libtorrent.rakshasa.no/")
[http://polishlinux.org/apps/p2p/rtorrent-console-p2p]("http://polishlinux.org/apps/p2p/rtorrent-console-p2p")
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")

rTorrent can be found in the repositories.

---

### Post by rogerp1 on 2007-08-25
Having tried all of them I prefer Ktorrent. Nice and simple and works straight away

---

### Post by stinger30au on 2007-08-25
> **mbt12 said:**
> I have no idea how to use torrents, but I think I am going to try.  What is a good torrent program I can use and also is there a site with a walkthrough? thanks

this is like going to a motorcycle forum of any kind and asking "whats the best spark plug" or "whats the best oil" or "whats the best tyres"

everyone has their own opinion.

the best torrent program to use is...


the one you feel the most comfortable using.

the one i like the most is qbittorrent

[http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)

---

### Post by misfitpierce on 2007-08-25
Deluge and Azureus... I say those b/c they are both great and have a way of blocking IP's as well as forced RC4 encryption

---

### Post by Harpoon on 2007-08-25
A small tangent:  Azureus and Bittyrant both have a "safepeer" plugin to block "known bad" ips--similar to PeerGuardian.  Is there a linux version hidden somewhere to use with the suggested alternatives?

Directly to the question, AZ works fine in Feisty, as does utorrent (lighter to be sure) when used with Wine.

---

### Post by gardara on 2007-08-25
I prefer rTorrent, it's light and powerful, good when you are leeching/seeding at high speed (1gbit connection in my case).

---

### Post by Dave Crowhurst on 2007-08-25
I have been using Transmission on my mac. 

[http://transmission.m0k.org/index.php](http://transmission.m0k.org/index.php)

[http://transmission.m0k.org/development.php](http://transmission.m0k.org/development.php)

Any Linux users using this?

[http://www.techystuff.info/?p=96](http://www.techystuff.info/?p=96)
> Transmission has been built from the ground up to be a lightweight, yet powerful BitTorrent client. Its simple, intuitive interface is designed to integrate tightly with whatever computing environment you choose to use. Transmission strikes a balance between providing useful functionality without feature bloat. Furthermore, it is free for anyone to use or modify.
Although Transmission isn&#8217;t currently in the Feisty repositories, I&#8217;ve created a .deb so you can install it effortlessly!

[http://techystuff.info/downloads/transmission_0.80-1_i386.deb](http://techystuff.info/downloads/transmission_0.80-1_i386.deb)


---

### Post by Harpoon on 2007-08-25
Thanks, Misfit.  I'll have to take a look at those options.

---

### Post by chessercizes on 2007-08-25
i used ktorrent a while ago, but now i mostly stick with uTorrent through wine.

Works like a charm for me =)

---

### Post by stoffe on 2007-08-26
IMO Deluge has become the absolute best torrent program (I'm using 0.5.4.1). It's about as powerful as uTorrent and not far behind Azureus, while being much easier to use than both (easier than anything I've tried, in fact). Your mileage may vary depending on what you like and what your needs are.

---

### Post by hyper_ch on 2007-08-27
Have you tried rTorrent yet?

---

### Post by phyrewall on 2007-08-27
> **Harpoon said:**
> A small tangent:  Azureus and Bittyrant both have a "safepeer" plugin to block "known bad" ips--similar to PeerGuardian.  Is there a linux version hidden somewhere to use with the suggested alternatives?

Directly to the question, AZ works fine in Feisty, as does utorrent (lighter to be sure) when used with Wine.

Why not run moblock? It's more stable than Peerguardian, uses BlueTack's lists, and is pretty lightweight. 

My votes are for deluge (for a linux build) and uTorrent w/wine (it's the one program I miss from Winblows)

---

### Post by rahimveron on 2007-08-27
My goat goes to Deluge.

---

### Post by phyzik on 2007-09-04
I've been recently having some strange problems with Deluge (torrents not downloading properly - speed going down to 0 every couple of seconds), the only application that could make me switch from uTorrent, so I tried this new open-source firefox extension, [FoxTorrent]("http://www.foxtorrent.com/").

I didn't experiment too much with it, but it looks ok. What do you guys think?

---

### Post by siralphred on 2007-09-04
if you have a fairly new pc azureus is good, or you can use utorrent with wine

---

### Post by AndyCooll on 2007-09-04
I tried KTorrent and quite liked it, however I get much better download speeds with Azureus and this is what gets my vote. Both Azureus (which also has a Windows version) and KTorrent are very easy to get to grips with. 

The torrent client that comes with Ubuntu is fine for the occasional torrent, but for any serious torrent use you'll be wanting to try one of those mentioned in this thread.

:cool:

---

### Post by Zoiked on 2007-09-04
qBittorrent is the best; Hands Down! : [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

Its fast, easy, and has a great GUI that is very similiar to uTorrent. :D Try it.

---

### Post by hyper_ch on 2007-09-05
> **AndyCooll said:**
> I tried KTorrent and quite liked it, however I get much better download speeds with Azureus and this is what gets my vote. Both Azureus (which also has a Windows version) and KTorrent are very easy to get to grips with. 

The torrent client that comes with Ubuntu is fine for the occasional torrent, but for any serious torrent use you'll be wanting to try one of those mentioned in this thread.

:cool:

did you enalbe uPnP in KTorrent?

---

### Post by joeashcraft on 2007-09-05
I use TorrentFlux and rtorrent.
rtorrent & screen are a winning combination. even if you log out of your DE, your torrents will still download :)
you can SSH to your computer and check on them, too.
TorrentFlux is awesome as well. I like it because I can let friends (who are on a college campus that doesn't allow torrenting) use it, and I can access it from any computer with internet (even the one from work :D)

all three programs mentioned (rtorrent, screen, torrentflux) are in the repos.
happy torrenting

---

### Post by AndyCooll on 2007-09-05
> **hyper_ch said:**
> did you enalbe uPnP in KTorrent?

Hmmm ...good question. I think so, however in all honesty I can't remember. It's ages since I last  used it.

:cool:

---

### Post by hyper_ch on 2007-09-06
well, check UPnP if you are behind a router... in kTorrent and the router :)

---

### Post by [Alsharifi] on 2007-09-06
> **Zoiked said:**
> qBittorrent is the best; Hands Down! : [http://qbittorrent.sourceforge.net/](http://qbittorrent.sourceforge.net/)

Its fast, easy, and has a great GUI that is very similiar to uTorrent. :D Try it.


X2 most efficient and best looking,also very easy to install.


```
sudo gedit /etc/apt/sources.list
```


then add these to the end.

```
deb http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/feisty/ ./
```

save exit.

_______

then.


```
sudo apt-get update
sudo apt-get install qbittorrent
```

and then go Download!

---

### Post by tcoffeep on 2007-09-06
I prefer Deluge :)

---

### Post by Psycho_Mantis on 2007-09-06
Used azureus in XP, but it constantly crashes in Ubuntu.
Now using Ktorrent. Will try rTorrent ..

---

### Post by Chilongola on 2007-09-08
How do you get torrents to open in Deluge.  When I click on a torrent it is opening in download manager.  In Ktorrent it works very good.

---

### Post by tcoffeep on 2007-09-09
I use Deluge every day, and it's always just loaded for me...*is confused*

---

### Post by Chilongola on 2007-09-10
Had to do a re-install.  It now works perfect.  Before that I loaded Azureus.  Not impressed at all.

---

