---
title: "Rtorrent trouble"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by lamtab on 2007-11-07
I have just installed rtorrent but i cant get things working.
I load the torrent file and after the hash chekc i get 
Tracker: [couldn't connect to server]
Any hints?

---

### Post by FG123 on 2007-11-07
Do you have the necessary ports forwarded, or if you're using UPnP, is it enabled on your modem/router?

Also, keep in mind sometimes trackers go down for many reasons, often due to heavy load. Try again later if everything else is working.

---

### Post by lamtab on 2007-11-07
I used azureus before and everything used to work fine so there's nothing wrong with my modem configuraton.
As for the ports i have this line:
port_range = 16778-16788
in the rtorrent.rc

---

### Post by airtonix on 2007-11-09
but do you have a rule on your router that does this : 

any data coming to router on ports 16778-16788 from internet.....forward it on to the computer 192.168.0.30 in my local network on thats computers  ports : 16778-16788.

btw i use this to start rtorrent up : 

rtorrent -p 9999-9999 -d ./downloads

and i use this to provide a status update for my housemates.

[http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/](http://www.g-loaded.eu/2007/06/23/rtorstat-a-simple-rtorrent-status-web-page-generator/)

---

