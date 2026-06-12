---
title: "bittorent question"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-19
Where do I store the files when it asks. Has it to be a shared folder?

---

### Post by justleen on 2007-09-19
for you, as user, to save the file:
it has to be a folder to which your current user has write access to.
Normally, your /home or any /data/  or /media/data disks you might have


for me, as other bittorrent user:
any where where your user has read access...
(say you started the torrent as root, then it will still be shared.

---

### Post by philinux on 2007-09-19
So just save the file to my desktop is fine then?

Is the preloaded Bittorent the best app?

---

### Post by PmDematagoda on 2007-09-19
BitTorrent is stupid, you should get Azureus. It's the best for me.

---

### Post by raijinsetsu on 2007-09-19
BitTorrent is probably the most stable on linux. I always have trouble with Azureus on linux only. Currently, I use TorrentFlux, which uses bittornado to do the actual downloading.

---

### Post by aninaiian on 2007-09-19
It does what it needs to do.  However, there are better clients out there.

I personally use deluge which has a utorrent feel.  There's Ktorrent for the kde users which also feels utorrent-like.  There's bittornado which is lightweight and stable.  There's azureus for those who want all the options at the cost of resources.  There's also rtorrent if you like the commandline.  If you really wanted to, you could even run utorrent through wine.

It all really depends on what you what your torrent client to do...

---

### Post by philinux on 2007-09-19
ok lets stick with azureus for now as.
azureus testing port 22403 nat error.

I've opened port 22403 in my router but firestarter says rule for bittorent is 6881-6889.
azureus says port 6880 reserved or something

[edit] and azureus keeps crashing doh

---

### Post by misfitpierce on 2007-09-19
If you want another light client like bittorrent but way better and my favorite I might add. Try Transmission.

[http://getdeb.net](http://getdeb.net) and search transmission. Best Torrent program out there and ultra light. Talking maybe 5MB ram light.

---

### Post by beyboo on 2007-09-19
Prefer not to mess up your deskop. I would advise  creating a downloads folder in your home folder and direct all torrent downloads there. 

I personally use deluge for torrent download. Its a simple and very fast client. I've been a utorrent user on Windoze and see the same power packed performance as from utorrent, although a bit less features on the interface !

[http://www.deluge-torrent.org]("http://www.deluge-torrent.org")

Assuming that you are not new to torrent technology. If you are do your port forwarding on the router as well as load firestarter firewall in ubuntu to add a  policy to take care of your forwarded torrent ports.

---

### Post by beyboo on 2007-09-19
> **philinux said:**
> ok lets stick with azureus for now as.
azureus testing port 22403 nat error.

I've opened port 22403 in my router but firestarter says rule for bittorent is 6881-6889.
azureus says port 6880 reserved or something

[edit] and azureus keeps crashing doh

Azureus is krazy !! dont waste ur life around it. It hogs the processor and memory - Try deluge or transmission - good stuff.

As for firestarter - add a new policy to the policy tab to take care of it. Dont worry if bittorrent protocol shows the default ports. thats normal

---

### Post by justleen on 2007-09-19
i found deluge very good... the first client i used that doenst have to "warm up like a freaking diesel engine!"

---

### Post by tenjin1 on 2007-09-19
> **beyboo said:**
> Azureus is krazy !! dont waste ur life around it. It hogs the processor and memory - Try deluge or transmission -l

I agree Azureus is too way to hard on your system just for downloading torrent files. Deluge is nice. Depending on what kind of interface you want...I use Bittornado. (simialr to the Bittorrent gui default client in ubuntu)You can install it from Automatix or from terminal:
```

sudo aptitude install bittornado bittornado-gui

```

Or Deluge (similar to utorrent gui):
```
wget [http://download.deluge-torrent.org/ubuntu/feisty/0.5.5/deluge-torrent_0.5.5-1_i386.deb](http://download.deluge-torrent.org/ubuntu/feisty/0.5.5/deluge-torrent_0.5.5-1_i386.deb) && \
sudo apt-get install libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-thread1.33.1 && \
sudo dpkg -i deluge-torrent_0.5.5-1_i386.deb && \
rm  deluge-torrent_0.5.5-1_i386.deb
```

---

### Post by philinux on 2007-09-19
Thanks all - ditched azureus installed deluge. now for the ports ah....

---

### Post by beyboo on 2007-09-19
> **philinux said:**
> Thanks all - ditched azureus installed deluge. now for the ports ah....

Way to go - Dont worry we are watching over you if you need help ;)

---

### Post by beyboo on 2007-09-19
[QUOTE=justleen;3390551doenst have to "warm up like a freaking diesel engine!"[/QUOTE]

:lolflag: - I am gonna use this  some place - I hope its LGPLed ;)

---

### Post by philinux on 2007-09-19
ok ticked random ports. 
[edit] ok works out the box no port fidling on router or firestarter!

what about upload speed etc

---

### Post by tenjin1 on 2007-09-19
Your download rate is proportional to your upload rate.

Depending on what internet connection you are using (i.e. cable, dsl, etc) is what you want to set your download/upload speed to.

I have Cable and have mine set to:

Download: 384 Kb/s
Upload: 36 Kb/s

and get good download speeds..the highest I've seen it get is +500 Kb/s download..but that also depends on how many seeders you are connected to.

You can test your broadband speed at [http://www.speedtest.net/]("http://www.speedtest.net/")

1. Maximum upload speed

Probably the most important setting there is. Your connection is (sort of) like a pipeline, if you use you maximum upload speed there’s not enough space left for the files you are downloading. So you have to cap your upload speed.

Use the following formula to determine your optimal upload speed…

80% of your maximum upload speed

so if your maximum upload speed is 40 kB/s, the optimal upload rate is 32kB/s

..And keep seeding!

2. Maximum download speed

Although setting your maximum download speed to unlimited may sound interesting, in reality it will only hurt your connection. If you still want to be able to browse properly, set your maximum download speed to:

95% of your maximum download speed

so if your maximum download speed is 400 kB/s, the optimal download speed is 380kB/s

3. Maximum connected peers per torrent

Yet another setting that you don’t want to max out. I experimented quite a lot with the max connected peers settings and came to the conclusion that both high and low number hurt the download speed of a torrent. The following setting worked best for me.

upload speed * 1.3

so if your maximum upload speed is 40 kB/s, the optimal amount of connected peers per torrent is

40 * 1.3 = 52

I didn’t noticed a difference for fast or slow connections here.

4. Maximum upload slots

1 + (upload speed / 6)

so if your maximum upload speed is 30 kB/s, the optimal number of upload slots is

1 + (30 / 6) = 6

---

### Post by philinux on 2007-09-19
Deluge is really professional looking piece of kit.
These are the settings it set. also what about the tickbox queue torrents to bottom when they begin seeding?

---

### Post by tenjin1 on 2007-09-23
I think as long as you use the reference above I posted you should be ok and get good upload/download sppeds using Bittorrent

---

