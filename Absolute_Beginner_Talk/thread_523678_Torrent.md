---
title: "Torrent"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by osiris.osiris on 2007-08-12
I have tried Azureus, bittornado client, and now I am testing uTorrent (using Wine), but I can't reach an appropiate download speed. I have a fast internet connection, and using Windows I've reached between 100 and 300 kB/s, but in Ubuntu the fastest speed I've reached is around 30 kB/s, that's the reason for use Windows. 

It will be helpfull for me if someone give me an idea.
Thank you in advance.
:popcorn:

---

### Post by 1/0 on 2007-08-12
Using any MS code is something I really try to avoid. I don't know why the speed loss but I can tell you this. Torrents are not the best way to measure speed. It could be that the torrent's just slower. 

As for a client I suggest you give Deluge a try. What was the reason you dumped Azureus and Bittornado, btw?

[edit] Ktorrent is good as well as rtorrent, the latter being terminal based. Ktorrent comes with KDE dependencies if that is of concern. [/edit]

---

### Post by tgrisier on 2007-08-12
Even though I use Gnome most of the time I use KTorrent about 99% of the time and love it.  You may want to look into that.

---

### Post by osiris.osiris on 2007-08-12
I've already installed Ktorrent and I'm using it, 2 torrents are downloading. The speed is slow. Can you help me to increase this speed changing the settings?

---

### Post by tgrisier on 2007-08-12
> **osiris.osiris said:**
> I've already installed Ktorrent and I'm using it, 2 torrents are downloading. The speed is slow. Can you help me to increase this speed changing the settings?

Well, slow is a relative term.  What kind of speed are you getting and on what type of connection?  The speed will also depend on the connection of the seeders/leechers.

---

### Post by Licurgo on 2007-08-12
Osiris.osiris:
First I used Ktorrent, then I realized that it was really slow, then if I can I avoided it, I prefer to use Kget, but **BE AWARE** of Ktorrent: it leaves an open port and hackers can get in

---

### Post by osiris.osiris on 2007-08-12
Well, i have a 3MB internet conection. One of the files i am downloading have 100 peers. That's the only thing  i now

---

### Post by 1/0 on 2007-08-12
I take it you have a firewall? Are the ports open and have you stated them in the client? Are the speed settings ok?

---

### Post by pnix on 2007-08-12
I use utorrent and get full speed. I think your problem is not torrent client. May be try to check portforward in your router.

---

### Post by dmlc133 on 2007-08-12
I'm in the same boat as osiris - I have tried Azureus, rtorrent and Deluge and can't get over 60kb/s absolute maximum download speed - most of the time it's around 35kb/s

I've never used any bittorrent programs before (on Windows or Linux) and although I do know a bit about general networking I don't really know what I should be looking for to optimise my torrent experience - any advice or pointers would be really appreciated.

I have tried setting up port forwarding though my router doens;t make it very clear - how can I check if it's working?

Thanks.

---

### Post by 1/0 on 2007-08-12
Some routers, especially cheep ones can't take the network load with torrents. I replaced my D-Link 604 with a Smoothwall on a P3. The speed dramatically increased. 

That doesn't seem to be the case for Osirius as he/she had it working before. A torrent can have hundreds of connections going at the same time compared to DC with just a few. Check the specifications of your firewalls and look for the throughput. It was 40 Mbit/s on the 604, which according to the D-Link tech support is good for downloading maybe one torrent at a time...

---

### Post by ron999 on 2007-08-12
Hi
I have used Azureus in the past and now use ktorrent.
The way that I check things is to try downloading a known good torrent, such as the Ubuntu 7.04 iso.
It maxes out my modem at around 240KB/s which (when multiplied by eight) gives around 2Mbps, which is what I'm paying for.
You can get the torrent from here, at the bottom of the page:-[http://releases.ubuntu.com/7.04/]("http://releases.ubuntu.com/7.04/")

---

### Post by 1/0 on 2007-08-12
> **ron999 said:**
> It maxes out my modem at around 240KB/s which (when multiplied by eight) gives around 2Mbps, which is what I'm paying for.

Lucky you I only got up to 790 Kb/sec which is not what I payed for... ;-)

---

### Post by dmlc133 on 2007-08-12
Ron that's really helpful advice - I tried that torrent and the download rate went through the roof (800KB/s) so (sorry this is such a stupid question) presumably that means the torrents I've tried so far are not very good ones? What's the best way to assess the quality of a torrent when searching?

Thanks again

---

### Post by ron999 on 2007-08-12
> **1/0 said:**
> Lucky you I only got up to 790 Kb/sec which is not what I payed for... ;-)
That's fine for dial-up:lol:

---

### Post by tgrisier on 2007-08-12
> **dmlc133 said:**
> I have tried setting up port forwarding though my router doens;t make it very clear - how can I check if it's working?

Have you checked the [info here]("http://www.portforward.com/")?

---

### Post by osiris.osiris on 2007-08-12
It's a good idea, i have tried it and the download speed had been about 300 kB/s, so i think that my conexion, my firewall and my router works properly

---

### Post by por100pre1 on 2007-08-12
Is the port actually open? You can install Firestarter, a tool for configuring the firewall included in Ubuntu:

```
sudo apt-get install firestarter
```

[Here's]("http://www.fs-security.com/docs/policy-page.php") how to open the posts with it. After configuring close Firestarter. Hope it helps. :)

---

### Post by osiris.osiris on 2007-08-12
No i haven't, but i think if the port is close, the down load speed will be 0 kb/s.
is that affirmation correct?

---

### Post by MenZa on 2007-08-12
> **osiris.osiris said:**
> No i haven't, but i think if the port is close, the down load speed will be 0 kb/s.
is that affirmation correct?

Yes, that sounds right, as nothing will be able to pass in- or out of it.

Also, if you're using GNOME, I highly recommend trying out [Deluge](http://deluge-torrent.org/). they even have pre-built packages for [Feisty](http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.4.1/&file=deluge-torrent_0.5.4.1-1_i386.deb) (amd64 packages [here](http://download.deluge-torrent.org/index.php?dir=ubuntu/feisty/0.5.4.1/&file=deluge-torrent_0.5.4.1-1_amd64.deb))

---

