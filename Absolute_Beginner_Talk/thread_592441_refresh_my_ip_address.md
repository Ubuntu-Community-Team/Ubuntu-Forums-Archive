---
title: "refresh my ip address"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by arkara on 2007-10-26
i want to download a big file from rapidshare. so it is fragmented and i want to refresh my ip address how do i do that from the command line???i friend of mine gave me a script but its for windows 

rasdial /disconnect

ipconfig /flushdns

ipconfig /release

ipconfig /renew


how can i make the same thing in linux?i need to restet my router via the terminal

---

### Post by agurk on 2007-10-26
I'd try:

sudo ifdown eth0
sudo ifup eth0

---

### Post by jualin on 2007-10-26
You could also just disconnect the power supply from your modem for about 5 seconds and then plug it back in  again. That is what I do to download in rapidshare. The modem would disconnect and get a new IP Address in seconds.

---

### Post by jualin on 2007-10-26
The problem with those commands is that sometimes they do not work. Another way of getting a new ip address is going to the web based modem setup and disconnecting from the ISP from there. Usually you can access to this function in most modems by typing in the address bar something such as 192.168.1.254 (depending on your modem). This will take you to the modem web based setup and from there you could tell your modem to disconnect from the internet and then to connect again.

---

### Post by adityakavoor on 2008-01-15
But for modems that do not support this system , command line would suit better.

Any Idea how to do ???

---

