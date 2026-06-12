---
title: "YABitTorrent Thread. 0KB/s xfer rate."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Larsen on 2007-08-08
Distro: 6.06LTS
Client: Default Gnome.bittorrent  EDIT: Now KTorrent as well.
Equipment I-Burst broadband modem connected via Ethernet.
Dialer : RoaringPenguin-PPPoE
Firewall: 0xHardware 1xSoftware(IPTables+Firestarter)

Firewall Configuration via firestarter
Restrictive by default. EDIT: Changed to permissive with slight improvement.
Port 80 (HTTP) Allow outbound and replies.
Port 443(HTTPS) Allow outbound and replies.
Port 6881-6889 (Bittorrent) Allow Outbound and Inbound(both replies and connections).

Well this didn't work.
So I downloaded KTorrent. and enabled port 4444 as well as it says to.
I like this client better it tells me stuff.

I changed outgoing connection to permissive and YAY! I'm in business, Oh hang on, no I'm not, it's identifying and connecting to computers but they all read as "choked" and about a minute later as "SNUBBED".

The test file has 89 seeds and 10 peers, multiple torrents have also been tried.
No effect.

Any suggestions?
I have tried multiple torrents. 
I have tried Off peak times. 
I have tried multiple clients.

Larsen

---

### Post by MenZa on 2007-08-09
It's possible your ISP is throttling any torrent downloads. I've seen that before.

---

### Post by Larsen on 2007-08-09
SOLVED: Sort of.

WORKING PORT CONFIGURATION (FOR ME)

Port 4444 (incoming and outgoing) enter the port manually in firestarter,
Port 6881-6889(named bittorrent in firestarter) (incoming and outgoing).
Outbound connections: Set to permissive.
Remember to hit "Apply settings"

Reboot system
Restart Firestarter
Run Ktorrent, 
Start your download.

Voila one perfectly good if sluggish Bittorrent system,
And maybe not so sluggish, well see how it goes after midnight :D
Between 4PM and 6PM in the arvo I was stuck on 56Kb/s about 5to6KB and not a single bit higher. (this is a 1Mb/s connection). So I sense the  ISP's fingers in that.

? Is there anyway to enable a greater range of ports in KTorrent i.e. 6881-6889 rather than just 6881.
? Does KTorrent have packet encryption?

Thanks for your suggestions.
Hopefully this will prove helpful to anyone else having problems.
Regards,
Larsen

---

### Post by Larsen on 2007-08-16
OK I tried it again this afternoon an I am at 100KB/s.
But I havent changed everything.

I think I must have had 2 dud torrents, it's working fine now.
Configuration as above.

Larsen.

---

