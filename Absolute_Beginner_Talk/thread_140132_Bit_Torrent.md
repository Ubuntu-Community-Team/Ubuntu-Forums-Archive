---
title: "Bit Torrent"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-03-05
Hi,


ever since the last upgrades from Ubuntu Ive been having real problems with Bit Torrent....

Everytime I try and download something it comes up with the error:

"Problem connecting with tracker"

I wondered if anyone knows how to fix this please?

Thanks

---

### Post by MadL on 2006-03-05
Hmm. Is your Internet connection behaving OK otherwise? This was on the [BitTorrent FAQ](http://www.dessent.net/btfaq/) page:

> [b]Problem connecting to tracker - timeout exceeded
Problem connecting to tracker - HTTP Error 503: Connect failed
Problem connecting to tracker - [Errno socket error] (10061, "Connection refused")
Problem connecting to tracker - (111, 'Connection refused')[/b]
    There was a problem contacting the tracker. Trackers tend to be heavily loaded, and connections sometimes fail. The best thing to do is just be patient and leave the client open. If you find you're getting this a lot, you can try increasing the HTTP request timeout by adding the parameter "--http_timeout 120" (the default is 60, unit is seconds.) See the section on changing the command line if you need help doing this.
**Problem connecting to tracker - HTTP Error 400: Not Authorized**
    This indicates that the administrators of this tracker are not allowing it to be used for this torrent. Some trackers will only track torrents that are also posted in their forums/website, for example. Usually this indicates a stale torrent -- try going to the web site associated with the tracker and see if you can find an updated torrent.
**Problem connecting to tracker - HTTP Error 404: Not Found**
    Probably a stale torrent. Try to find a new link to the torrent.
**Problem connecting to tracker - HTTP Error 407: Proxy Authentication Required**
    You may need to configure a username and password for your proxy server setting in order to contact the tracker. See this section for details.

Have you tried downloading torrents from a few different sources? The problem might be on their end. If you've got BT set for the traditional ports (6881-6889), some trackers are starting to reject those, so you may need to set BT to use different ports (the latest version of BitTornado uses ports 10000-60000 as its default). If you've got Firestarter running, check to make sure it's allowing access to BitTorrent for the ports it needs (**Edit:** To do this, open up Firestarter and click the "Policy" tab. There should be an entry under "Allow Service" for the ports you're using).

Hope this helps. Good luck.

---

### Post by Dr Von Bon Bon on 2006-03-05
thanks, 

My internet is behaving fine.
I've tried from several sources and that also doesnt work.

How do I go about changing the ports please, I'm using the normal bittorrent that comes with Ubuntu

---

### Post by MadL on 2006-03-05
I've been using BitTornado, so I'm not familiar with the default version Ubuntu uses. Taking a quick look at its [home page](http://gnome-bt.sourceforge.net/), it looks like a bare-bones implementation of BT that may not let you change the ports it uses (someone please correct me if I'm wrong on this). 

You may want to try using one of the other BitTorrent services. I've been using BitTornado lately (you can use Synaptic to get it -- be sure to install both bittornado, part of the default repositories, and bittornado-gui, which is part of the Universe repository). A lot of people also like Azureus (you can use Automatix to install this), although it gave me problems.

Only other thing I can think of is that maybe your ISP's begun throttling BitTorrent. The timing, though, is a little too coincidental for that, if the problems only began after you updated Ubuntu. Do you happen to remember exactly what was updated?

---

