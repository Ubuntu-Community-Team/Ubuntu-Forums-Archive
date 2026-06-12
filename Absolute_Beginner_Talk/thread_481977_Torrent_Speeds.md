---
title: "Torrent Speeds?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by lepz on 2007-06-23
What determines torrent download speeds? It cant be just the number of peers/seeds. I have had speeds of under 5KBs with 10+ peers and just now I had  500KBs with just one peer, so what else determines the speed and how can I always get 500KBs? ;)

---

### Post by Inxsible on 2007-06-23
Also depends on how fast the network connection of the seeder is. also on your own network speed. Last but not least also the number of nodes that the packets have to travel from the seeder's computer to yours.

Other factors may include, firewalls on your or the seeders side. Open ports on either side. 

There are some factors you can control, some which the seeder can control and some which none can. :)

---

### Post by lepz on 2007-06-23
> **Inxsible said:**
> Also depends on how fast the network connection of the seeder is. also on your own network speed. Last but not least also the number of nodes that the packets have to travel from the seeder's computer to yours.

Other factors may include, firewalls on your or the seeders side. Open ports on either side. 

There are some factors you can control, some which the seeder can control and some which none can. :)

I normally have firestarter running if I'm downloading a torrent, but don't know what else I can do at my end to speed things up?

---

### Post by Famicommie on 2007-06-23
If you have the necessary ports open on your firewall (for regular BT protocol and DHT), then that is really all you can do.

Since some people are on networks at Universities and such, they are able to distribute very rapidly due to their alloted upload bandwidth.

Sometimes there will be visible seeds (like that swarm of 10 you mentioned) where the seeders are busy seeding other torrents to people, or they are downloading several files and have hit their maximum number of connections.

---

### Post by lepz on 2007-06-23
> **Famicommie said:**
> If you have the necessary ports open on your firewall (for regular BT protocol and DHT), then that is really all you can do.

Since some people are on networks at Universities and such, they are able to distribute very rapidly due to their alloted upload bandwidth.

Sometimes there will be visible seeds (like that swarm of 10 you mentioned) where the seeders are busy seeding other torrents to people, or they are downloading several files and have hit their maximum number of connections.

This is where I have problems, (forwarding ports) I'm still unsure about this.I use Ktorrent and any info would be appreciated.

---

### Post by Famicommie on 2007-06-23
I've never used ktorrent, but it should have documentation telling you which ports you need to forwards.

As for how to forward them, you'll need to configure that via firestarter and via your router.

---

### Post by lepz on 2007-06-23
Ok thanks anyway :)

---

### Post by Golyadkin on 2007-06-23
Generally you can choose the ports you want to use yourself, mostly one for TCP and one for UDP. It is also advised not to use 6881-6889 as ports because several ISPs started blocking or throttling those ports because they are known BitTorrent ports. Use something else, as long as it is > 1024

---

### Post by Inxsible on 2007-06-23
Here are a few links on port forwarding. See if they help you out

[http://p2p.weblogsinc.com/2005/04/24/how-to-configure-your-router-to-allow-fast-bittorrent-downloads/](http://p2p.weblogsinc.com/2005/04/24/how-to-configure-your-router-to-allow-fast-bittorrent-downloads/)

[http://userpages.umbc.edu/~hamilton/btclientconfig.html](http://userpages.umbc.edu/~hamilton/btclientconfig.html)

---

