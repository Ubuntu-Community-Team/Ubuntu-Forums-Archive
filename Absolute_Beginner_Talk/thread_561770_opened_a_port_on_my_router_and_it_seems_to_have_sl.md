---
title: "opened a port on my router and it seems to have slowed down torrent download .."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-09-28
.. rather than speeded it up.

i have the correct instructions on how to set up my router for utorrent [here]("http://portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882v2/Utorrent.htm").

i've entered a port number in utorrent and unchecked 'enable upnp mapping' as instructed, and i've entered the static ip as 192.168.1.3, but i'm not too sure if this is actually correct

i think it is .. if i do ifconfig, i get the inet addr on 'eth0' as 192.168.1.3, but it also gives a Broadcast address of 192.168.1.255 so i wondered if i should enter that into the redirect part of the router setup instead of 192.168.1.3 ???

aannyway, when i fire up utorrent under wine, the download speeds seem to have bottomed out at between 5.0kb/s to 10.0kb/s.

before i actually opened the port on the router, i was actually getting around 15kb/s, but the network indicator on utorrent was red, and said the port wasn't connectable and couldn't receive incoming connections - now it's a green tick, it just seems to have slowed right down instead of going the other way.

the torrent i'm downloading has 160 dht connections, 59 active seeds and 13 peers.  With 59 seeds, it should usually be at least 30kb/s downloading.

hope that's enough information and someone can give me a clue !

thanks :D

---

### Post by nixclusive on 2007-09-28
doing ifconfig while having a router between you and the internet gives you your *private* IP address. Visit a site like [whatismyip](http://www.whatismyip.com) to check out your *public* IP address. Hope this clears some things for ya :-)

---

### Post by jasonwatkins on 2007-09-28
i went to that site and tried entering the IP address it gave me into the router to forward the port, rebooted the modem and fired up utorrent, and i get a "listen error" on the network indicator.

if i enter 192.168.1.3 and the port I want forwarded, i get the green tick to say it's ok, so i'm assuming that this is the correct IP

i'm just sure it should be downloading quicker ...

---

### Post by Whiffle on 2007-09-28
Try using ktorrent.  If it downloads faster, it may be a problem with using wine+utorrent (although that may work fine, i'm not familiar with that since ktorrent works fine for me...:D )

Another thought is you may have an issue like described here:
[http://blog.williamts99.com/index.php?/archives/218-DD-WRT-and-Bittorrent-or-other-P2P-apps.html](http://blog.williamts99.com/index.php?/archives/218-DD-WRT-and-Bittorrent-or-other-P2P-apps.html)

---

### Post by jasonwatkins on 2007-09-28
i'm going to go back to using deluge since i was using that regularly in the first place with no problems - i've been trying to work out how to set it up so that it doesn't upload 3 times as much as it downloads but to no avail.

fired up deluge and running at the moment ..

31 seeds, 44 peers with a download speed wildly fluctuating between 7.5kb/s and 45.0kb/s

so since it's 5:45am here in the UK, i think i'll leave it running for a while and go back to bed :D

---

