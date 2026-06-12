---
title: "What is Bittorrent?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by bonzodog on 2006-02-25
I know this is going to sound amazing coming from a staff member, but while I have **alot** of experience using linux, having had it as my home OS since 1999, and I have been using the internet since 1996, my experience at file downloading consists mainly of ftp use. 
I have used ed2k, kazaa, and napster, and I get the idea of getting bits of files from different places, but I cannot for the life of me use bittorrent as I don't know how to start it. 
With ed2k etc, there has been a graphical client with a list of servers, and I just clicked 'connect' then 'search'. However, when I tried to start the bittorrent thing in the menu, it asked for a seed? WTH?. 
I always have to use ftp to get ISO's as I have NO understanding of bittorrent or how to use it. 
Can some one **PLEASE** post a beginners guide to using and setting up bittorrent in Ubuntu, and I will add it to the Doc Facility, and I might even start using it. :D

---

### Post by SavageBeginner on 2006-02-25
You need to go to a website that has torrent seeds for the file you wish to download.  I suggest a google search for torrent.

Bittorrent basically lets you upload the file to others as you download it.

---

### Post by stoeptegel on 2006-02-25
I'll try to write a short introduction.

Bittorrent works with hashsums to check each piece of the data you're downloading, this is build into *.bittorrent files and your clients checks every piece on the fly. As soon as is doesn't match it will trash the piece and tries to re-download it. These pieces (which are divided in chucks) can go from 32 KB to 4MB. ( controll <--> overhead )

These *.bittorrent files are shared on websites or trackers. There is also a second way of sharing, the DHT network, which works much like the way as kademlia does on edonkey where you can "bootstrap"  into the network by contacting a server on bittorrent.com.

So there basicly are two ways of using bittorrent, by trackers (with the advantage of tracking abuse and have a closed community) and DHT (with the advantage of a more stable network).

---

### Post by Kurt` on 2006-02-25
Wikipedia explains it very well:

[http://en.wikipedia.org/wiki/Bittorrent](http://en.wikipedia.org/wiki/Bittorrent)

I have been using Bittornado, so:

apt-get install bittornado

After that, just download a .torrent file and double click it!

(On windows, I used Bitcomet. C++ > Python for handling large files, Python's CPU usage goes insane. I will install Azureus later, although I'm not a fan of Java)

---

### Post by Mr.X on 2006-02-25
BitTorrent is like Limewire/Kazaa/Most P2P connections, except that instead of like 9 etc "mirrors", there are now lots of people sharing the same file!
Download sites:
[www.torrentspy.com](www.torrentspy.com)
[www.isohunt.com](www.isohunt.com)

Make sure the bar is green(for torrentspy), then you will get the fastest downloads :)
Oh, and Azereus is quite nice :D

---

### Post by direwolf on 2006-02-25
Ubuntu comes with a BitTorrent client out of the box. 
The first step is to find the torrent you want to dl.  I like TWit, so I'll download last weeks TWiT as an example.  I go and find the .torrent file ...
[[IMG]http://img112.imageshack.us/img112/6092/bd12pf.th.png[/IMG]](http://img112.imageshack.us/my.php?image=bd12pf.png)
[[IMG]http://img240.imageshack.us/img240/7707/bd22do.th.png[/IMG]](http://img240.imageshack.us/my.php?image=bd22do.png)
and save it wherever I want. 

Then I start the BitTorrent client by going to Applications > Internet > BitTorrent
[[IMG]http://img112.imageshack.us/img112/8947/bt13jh.th.png[/IMG]](http://img112.imageshack.us/my.php?image=bt13jh.png)

It will ask me where the .torrent file I want to use is and I will browse to where I saved it, select it and click open 
[[IMG]http://img129.imageshack.us/img129/1948/bt27zj.th.png[/IMG]](http://img129.imageshack.us/my.php?image=bt27zj.png)

Then it asks me where I want to save the file I will download. I browse to where I want to save it and click save.
[[IMG]http://img129.imageshack.us/img129/8127/bt34li.th.png[/IMG]](http://img129.imageshack.us/my.php?image=bt34li.png)

It will then find peers (this can be seen in the "Events" tab) and start downloading
[[IMG]http://img130.imageshack.us/img130/3131/bt42gc.th.png[/IMG]](http://img130.imageshack.us/my.php?image=bt42gc.png)

I can cap how many upload connections and the upload bandwidth if I want to. 
[[IMG]http://img130.imageshack.us/img130/7046/bt56mr.th.png[/IMG]](http://img130.imageshack.us/my.php?image=bt56mr.png)

a couple of LEGAL torrent trackers are... 
[http://www.legaltorrents.com/](http://www.legaltorrents.com/)
[http://bt.etree.org](http://bt.etree.org)

I should also note that there are other Bit Torrent clients such as Bit Tornado and Azureus available for Ubuntu. They offer other more options through the gui such as what ports to use, whether or not to use portforwarding, etc. 

For those who would rather use the command line you can use that to download your torrents. 
[[IMG]http://img131.imageshack.us/img131/4668/btcli11vs.th.png[/IMG]](http://img131.imageshack.us/my.php?image=btcli11vs.png)
--max_uploads # (where # is the number of people you will allow to dl from you at a time)
--max_upload_rate # (the limit of bandwidth to allow - in KB/s) 
--ip 192.168.0.1 (where 192.168.0.1 is the ip you want reported to the tracker - other peers will still be able to see your real ip address)

much more detail and help for using cli is available by typing the command:
man btdownloadcurses

---

### Post by nickle on 2006-02-25
also see my post to your query in comunity chat:

[http://www.ubuntuforums.org/showthread.php?t=135910]("http://www.ubuntuforums.org/showthread.php?t=135910")

---

### Post by Buffalo Soldier on 2006-03-11
[http://computer.howstuffworks.com/bittorrent.htm](http://computer.howstuffworks.com/bittorrent.htm)

I guess torrent is one of the things that many people use but not everyone understands well.

---

### Post by pwner4once on 2006-03-18
[QUOTE=direwolf]Ubuntu comes with a BitTorrent client out of the box. 
The first step is to find the torrent you want to dl.  I like TWit, so I'll download last weeks TWiT as an example.  I go and find the .torrent file ...
[[IMG]http://img112.imageshack.us/img112/6092/bd12pf.th.png[/IMG]](http://img112.imageshack.us/my.php?image=bd12pf.png)
[[IMG]http://img240.imageshack.us/img240/7707/bd22do.th.png[/IMG]](http://img240.imageshack.us/my.php?image=bd22do.png)
and save it wherever I want. 

Then I start the BitTorrent client by going to Applications > Internet > BitTorrent
[[IMG]http://img112.imageshack.us/img112/8947/bt13jh.th.png[/IMG]](http://img112.imageshack.us/my.php?image=bt13jh.png)

It will ask me where the .torrent file I want to use is and I will browse to where I saved it, select it and click open 
[[IMG]http://img129.imageshack.us/img129/1948/bt27zj.th.png[/IMG]](http://img129.imageshack.us/my.php?image=bt27zj.png)

Then it asks me where I want to save the file I will download. I browse to where I want to save it and click save.
[[IMG]http://img129.imageshack.us/img129/8127/bt34li.th.png[/IMG]](http://img129.imageshack.us/my.php?image=bt34li.png)

It will then find peers (this can be seen in the "Events" tab) and start downloading
[[IMG]http://img130.imageshack.us/img130/3131/bt42gc.th.png[/IMG]](http://img130.imageshack.us/my.php?image=bt42gc.png)

I can cap how many upload connections and the upload bandwidth if I want to. 
[[IMG]http://img130.imageshack.us/img130/7046/bt56mr.th.png[/IMG]](http://img130.imageshack.us/my.php?image=bt56mr.png)

a couple of LEGAL torrent trackers are... 
[http://www.legaltorrents.com/](http://www.legaltorrents.com/)
[http://bt.etree.org](http://bt.etree.org)

I should also note that there are other Bit Torrent clients such as Bit Tornado and Azureus available for Ubuntu. They offer other more options through the gui such as what ports to use, whether or not to use portforwarding, etc. 

For those who would rather use the command line you can use that to download your torrents. 
[[IMG]http://img131.imageshack.us/img131/4668/btcli11vs.th.png[/IMG]](http://img131.imageshack.us/my.php?image=btcli11vs.png)
--max_uploads # (where # is the number of people you will allow to dl from you at a time)
--max_upload_rate # (the limit of bandwidth to allow - in KB/s) 
--ip 192.168.0.1 (where 192.168.0.1 is the ip you want reported to the tracker - other peers will still be able to see your real ip address)

much more detail and help for using cli is available by typing the command:
man btdownloadcurses[/QUOTE]

did u configure anything? 
because it's not going really fast for me at all. actually it's going at around 10kB/sec which is just too slow for DSL. i usually donwload around 150kB/sec in window. is there anyway to configure the ports and stuff?

---

### Post by Sef on 2006-03-18
> I know this is going to sound amazing coming from a staff member,

I don't think it was amazing.   Am sure everyone involved with Ubuntu has knows some things well, but not everything well.  As Will Rogers, the cowboy philosopher, once said, "You know everybody is ignorant, only on different subjects."

---

### Post by mackinax on 2006-03-18
Bittorrent is much easier to use and configure if you use a more advanced client than the basic one ubuntu comes with. Important things to consider when using bittorrent are: 

-- Have the correct ports forwarded if you are behind a firewall or NAT/router. bittorrent can work somewhat ok while you're firewalled or NAT'ed, but you will maximize potential by allowing traffic freely through forwarded ports. see - [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding) - [http://www.portforward.com/](http://www.portforward.com/)

-- Cap your upload rate in the bt client. Saturating your upload bandwidth will have a negative effect on your downloading rate. Set your maximum upload rate to 75-90% of your total upload capacity. (example, my cable connections max upload bandwidth is 300 kbps or 37.5 Kbps, so i set my max bt upload rate to about 32 Kbps) 

-- Lastly, you will only get fast downloads if there are enough peers that you can get good connections with. One peer may be able to feed you at 100 Kbps if you're lucky... or 40 peers may only be able to give you 5 Kbps if the connections aren't good. So, look for torrents with lots of seeders and peers whenever possible.

Try Bittornado at least, if not the more advanced Azureus.

---

### Post by Voullie on 2007-09-15
Hey,

I'm using  Bittorrent that comes along with feisty fawn but it seems I can only download one torrent at a time. Does anyone know how I can fix it so I can download several torrents simultaneously?

 /V

---

### Post by Maestro23 on 2007-09-15
> **Voullie said:**
> Hey,

I'm using  Bittorrent that comes along with feisty fawn but it seems I can only download one torrent at a time. Does anyone know how I can fix it so I can download several torrents simultaneously?

 /V

Check your preferences in the torrent client.

---

### Post by Voullie on 2007-09-15
Can't find the preferences. When I start Bittorrent from Applications->Internet I immediately get a window in which I'm supposed to choose a torrent to download. After choosing a file I get the download status window which has a very limited set of options and not the one I'm looking for.

  /V

---

### Post by Maestro23 on 2007-09-15
> **Voullie said:**
> Can't find the preferences. When I start Bittorrent from Applications->Internet I immediately get a window in which I'm supposed to choose a torrent to download. After choosing a file I get the download status window which has a very limited set of options and not the one I'm looking for.

  /V

What's the bit-torrent program you're using?  Do you have it setup to open a .torrent file from Firefox automatically?

---

### Post by bogolisk on 2007-09-15
> **Voullie said:**
> Can't find the preferences. When I start Bittorrent from Applications->Internet I immediately get a window in which I'm supposed to choose a torrent to download. After choosing a file I get the download status window which has a very limited set of options and not the one I'm looking for.

  /V

Use transmission, it just works!

[http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)

---

### Post by Majorix on 2007-09-15
> **Voullie said:**
> Hey,

I'm using  Bittorrent that comes along with feisty fawn but it seems I can only download one torrent at a time. Does anyone know how I can fix it so I can download several torrents simultaneously?

 /V

Probably you didn't update your feisty. There was a problem in the non-updated versions where you couldn't download more than one. If the problem persists, try gconf-editor and look for the settings of bittorrent from there.

---

### Post by Voullie on 2007-09-18
Quote Majorix:
*Probably you didn't update your feisty. There was a problem in the non-updated versions where you couldn't download more than one. If the problem persists, try gconf-editor and look for the settings of bittorrent from there.*

I found the Bittorrent properties in gconf-editor under apps->gnome-btdownload but it contains no more properties than if you run the application itself. I'm also not really sure what you're reffering to when you say "update your feisty". I've used Ubuntu only for a couple of weeks so I'm not really familiar with it yet.

/V

---

### Post by sazan on 2007-09-18
does microtorrent work with ubuntu as it does for windows ??

---

### Post by Maestro23 on 2007-09-18
> **sazan said:**
> does microtorrent work with ubuntu as it does for windows ??

If you're referring to utorrent, then no.  You must run it under WINE.

WineHQ: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by sazan on 2007-09-18
> **Maestro23 said:**
> If you're referring to utorrent, then no.  You must run it under WINE.

WineHQ: [http://www.winehq.org/](http://www.winehq.org/)

thanks

---

### Post by RobMBaker on 2007-09-25
Vouille, you were on the right track, I think.
Go back to the config and go down one more level, into gnomebtdownload->settings and look at the "max_port" and "min_port" setting. Mine were both set to the same port by default - I could be totally wrong here, but give it a go, it may work ...

:)

---

### Post by RobMBaker on 2007-09-25
Yep, I just checked - the port range does determine how many simultaneous connections you can have.
I changed my max_port to 10 ports higher than the min_port value; and now I can d/l multiple torrents, which I couldn't do before.

---

### Post by hyper_ch on 2007-09-25
I used to run kTorrent but now I switched to a console-client: rTorrent... I load it in screen and can easily control/manipulate it from wherever I am.

---

### Post by Voullie on 2007-09-28
Big thanx to  you, RobMBaker. It worked, why shouldn't it, it's totally logical. Can't believe I didn't think of it sooner.

Thanx! /V

---

### Post by SuperDuck on 2007-09-28
I've used Bittorrent to download .iso's of various distributions.  Some distros have the .torrent on their website, and it's usually been faster than downloading the same file from a mirror.

I've looked around for a few sites that offer a decent torrent selection without looking like a seedy site that I can't trust or isn't reliable.  It's hard because those are the ones that come up first in searches.

---

