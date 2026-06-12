---
title: "BTgaurd for Ubuntu"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ryrules1 on 2008-03-30
is there such a thing as BTgaurd for Ubuntu or a similar program so my isp isnt throttling my bittorrent download? or is there a way to hide what im downloading using other methods? I searched and came up with nothing.

---

### Post by c-ron on 2008-04-01
If I recall correctly, BTGuard is a proxy service (pay $$$), not software. 
Any BitTorrent client that lets you specify a proxy should work with their servers.

Also, forcing encryption for BitTorrent traffic may allow you to bypass your ISP's throttling without using a proxy.
In Transmission (Ubuntu's default BitTorrent client), you can select "Ignore unencrypted peers" in the preferences.

---

### Post by ryrules1 on 2008-04-03
I am using deluge, so what ports would you recommend i use? and is there a way to find out what ports are open?

---

### Post by x714x on 2008-04-03
If you got the extra cash just rent a server and use that to torrent. Then just ftp everything to your home computer.

BTW who is your ISP? comcast?

---

### Post by ryrules1 on 2008-04-04
yeah comcast.

---

### Post by brennydoogles on 2008-04-04
> **x714x said:**
> If you got the extra cash just rent a server and use that to torrent. Then just ftp everything to your home computer.

BTW who is your ISP? comcast?

How would one go about doing that? I have a ton of extra space on my godaddy server....

---

### Post by aeiah on 2008-04-04
servers designed for bittorrent use are called seedboxes. there are plenty of services around. i dont think you'd be able / allowed to do it with a regular web server package. usually seedboxes either have windows or linux installed, and you just VNC / remote desktop into them and set them up as you please by installing utorrent / rtorrent / torrentflux and an ftp application

deluge has an IP blocklist plugin that works like peerguardian, but that wont stop throttling, it'll just stop the *IAA snooping on you (in theory). deluge also has a 'require all connections to be encrypted' setting. im not sure what kind of throttling comcast does, it may be port based, or it may be packet type based. im guessing they can probably detect that the packets are bittorrent-esque packets and so it doesnt matter what port you're using :(

---

### Post by ryrules1 on 2008-04-04
I would love to buy some of you server space, how exactly do you go about doing that?

---

