---
title: "Bittorrent..."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by jwkungfu on 2008-04-02
Hi all, had a crack at firing up Bittorrent myself... failed...

john@john-laptop:~$ sudo apt-get install bittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bittorrent is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I can't find it under the GUI Applications/etc...

Can anybody advise further?

Cheers!

jw.

---

### Post by stefangr1 on 2008-04-02
Well, if it is installed you can just execute the command "bittorrent" to fire it up... did you already try that?

---

### Post by kpkeerthi on 2008-04-02
It should open automatically from within firefox when you click on a .torrent file. 

Alternatively try [deluge]("http://www.getdeb.net/app/Deluge") or [transmission]("http://www.getdeb.net/app/Transmission")

---

### Post by jwkungfu on 2008-04-02
No luck...

john@john-laptop:~$ bittorrent
bash: bittorrent: command not found

---

### Post by jwkungfu on 2008-04-02
> **kpkeerthi said:**
> It should open automatically from within firefox when you click on a .torrent file. 

Alternatively try [deluge]("http://www.getdeb.net/app/Deluge") or [transmission]("http://www.getdeb.net/app/Transmission")

Where are these .torrent files located?
I used to use Limewire when I was on M$ Windoze, recently I was using Nicotine, then had to do a full reboot (forgot password...doh!)
I would like to be able to download video & music again, is BitTorrent the right application for this?

---

### Post by Mick8882003 on 2008-04-02
search torrent in the ap installer, personally i use ktorrent, others will say other progs

---

### Post by jwkungfu on 2008-04-02
> **Mick8882003 said:**
> search torrent in the ap installer, personally i use ktorrent, others will say other progs

Many thanks,
When I looked Applications/Add/Remove and typed bittorrent, the application is there and it's box is checked with a tick...?
So why wouldn't it show up under Applications/Internet (for example?)

I'm downloading KTorrent as I type this...

How do I activate that when it has finished?

---

### Post by taavikko on 2008-04-02
> **jwkungfu said:**
> 
How do I activate that when it has finished?
If I remember correctly, the command is
```
gnome-btdownload
```

The basic torrent-client in gutsy and older versions doesn't have the rich features that many new clients features.

I recommend something like deluge, transmission(BTW default client in hardy) etc.

---

### Post by bumanie on 2008-04-02
I use deluge which ahs a deb package on their website [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)
Ktorrent, transmission are also meant to be good. In fact transmission is going to be included in hardy heron as the default bittorrent client.

---

### Post by jwkungfu on 2008-04-02
Hardy Herron is the next Ubuntu upgrade right?
Later in April?

---

### Post by aeiah on 2008-04-02
others have mentioned bittorrent clients that are good. id personally go with deluge or transmission. to get a general idea of how bittorrent works, check wikipedia. obviously we cant really tell you how to download music and video that you dont have the copyright for on this forum as its against forum rules, but wikipedia and google should give you an idea of what is involved and what to look out for in terms of seeds and leeches etc, and some popular bittorrent trackers

---

### Post by taavikko on 2008-04-02
> **aeiah said:**
> obviously we cant really tell you how to download music and video that you dont have the copyright

where have you got that idea that only thing that people downloads is copyrighted?
Bittorrent is gaining rapid popularity amongst services that sells or displays digital media,

---

### Post by stefangr1 on 2008-04-02
I think this is not the right place to discuss how downloading trough torrents works (even though you could theoretically also use it to download things that are legally), just google for it a minute and you'll find lots of stuff!

---

### Post by wieman01 on 2008-04-02
> **taavikko said:**
> where have you got that idea that only thing that people downloads is copyrighted?
Bittorrent is gaining rapid popularity amongst services that sells or displays digital media,
This is true. But pointing to illegal websites, etc. will not be tolerated in here. I think that's what the OP intended to say.

---

### Post by taavikko on 2008-04-02
> **wieman01 said:**
> This is true. But pointing to illegal websites, etc. will not be tolerated in here. I think that's what the OP intended to say.

I agree!, but I understood that the problem was just that for the starter of the thread, was difficulties understanding how the default client worked. and how to start it.

Personally i didn't see any links to any site that contains torrent files.

---

### Post by jwkungfu on 2008-04-02
> **Mick8882003 said:**
> search torrent in the ap installer, personally i use ktorrent, others will say other progs

Well, I just fired KTorrent up thru Applications/Internet and it seems a slick enough App for me!? Thanks!
I've had enough for one night (bit ill), will check it out in more depth tommorrow...

THANKS!!

---

### Post by c-ron on 2008-04-02
On a side note, bittorrent is the cli app.
You also need bittorrent-gui if you want a graphical front end.

---

### Post by stoneybroke on 2008-04-02
If you used Limewire on windows then try Frostwire for Ubuntu it is better.

---

### Post by bumanie on 2008-04-02
> **jwkungfu said:**
> Hardy Herron is the next Ubuntu upgrade right?
Later in April?

Hardy heron is due for release on the 24th of this month.

---

