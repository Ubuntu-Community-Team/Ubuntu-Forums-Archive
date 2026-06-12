---
title: "How can i remove/bloc kBitTorrent?  Security risk?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by marco123 on 2007-04-25
Hi.  I used BitTorrent to download a file yesterday, and ever since I get about 100 hits per minute to the firewall. 

 In the "Events"  tab of firestarter it says that it is bittorent, under services.  

 I tried shutting down the pc and  waiting a while then switching it back on, but it still happens.  When I tried to remove bittorrent it said I couldnt?

---

### Post by marco123 on 2007-04-25
OK.  Managed to uninstall bittorrent, but still having same problem??

Does anyone know anything else I can try, or if my linux system is in any danger from this continued probing?  At boot for example, before i can enable the firewall?

Thanks, marco

---

### Post by dreadlord_chris on 2007-04-25
> **marco123 said:**
> Hi.  I used BitTorrent to download a file yesterday, and ever since I get about 100 hits per minute to the firewall. 

 In the "Events"  tab of firestarter it says that it is bittorent, under services.  

 I tried shutting down the pc and  waiting a while then switching it back on, but it still happens.  When I tried to remove bittorrent it said I couldnt?

It says bittorrent under services because it's been told that that port belongs to bittorrent. It does not mean that bittorrent is *actually* running.

The reason you're continuing to receive so many hits to that port has to do with the way the torrent protocol works. When you downloaded your torrent file yesterday, you computers IP was added to that torrent's tracker(s) peer list. If this was a popular torrent (lots of seeders/leachers) it could take a while for your IP to drop off the tracker(s) list. Also, if you or any of the peers that were connected when you downloaded the torrent, were using DHT (dynamic host tracking - most current clients support it) this can dramatically increase the time your IP persists as a torrent peer.

that being said - there really is nothing for you too worry about - unless you start getting hits in the 10,000/minute you won't notice a thing except entries in a log.

If it really bothers you though, you could just change your IP (assuming it's not static): Usually turning your **modem** off for about 10 minutes is enough to get a new IP. Quite often just turning off the PC won't be enough to grab a new IP, since most broadband modem maintain a persistant connection to the ISP.

---

### Post by marco123 on 2007-04-25
Thank you very much for the answer, that makes things a lot clearer. :) 

So it will just stop happening after a couple of days or so?

---

### Post by marco123 on 2007-04-25
I have a dual boot with xp and ubuntu feisty, does that mean if I use bittorrent in windows it will start happening again in ubuntu?:confused:

---

### Post by dreadlord_chris on 2007-04-25
> **marco123 said:**
> I have a dual boot with xp and ubuntu feisty, does that mean if I use bittorrent in windows it will start happening again in ubuntu?:confused:

Well now, that really all depends on whether you retain the same IP when you reboot.

And yes, the hits will eventually taper off - but there's nothing to worry about in the mean time...

---

