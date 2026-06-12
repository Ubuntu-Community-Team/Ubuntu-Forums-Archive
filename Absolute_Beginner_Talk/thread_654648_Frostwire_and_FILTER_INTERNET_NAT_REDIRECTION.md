---
title: "Frostwire and FILTER INTERNET NAT REDIRECTION"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-31
Would turning on filter internet nat redirection on my router prevent people from being able to browse me, and download from me? If not, how would I accomplish this?

---

### Post by rivalarrival on 2008-01-01
From what I understand, the internet nat redirection feature allows you to use the public internet address to access machines while inside the network. For instance, your ISP provides 60.x.x.x to your router through the modem. Your server, inside the router, has a private address of 192.168.1.2. With the redirect enabled, you can access your server directly at 60.x.x.x. With the redirect disabled, you would have to go to 192.168.1.2. In other words, it does nothing about incoming traffic. 


It is pretty hard to prevent outbound bittorrent traffic. Not to say it can't be done, but I think it's a function of the application, not the network.  

It seems like the torrent trackers will order your application to upload to someone else. I've got a torrent client behind a firewall without forwarding the appropriate ports, yet it is still able to upload. (it does seem quite crippled, though...)

If the application won't allow you to prevent uploads, you'd have to set up a fairly sophisticated firewall to accomplish this.

---

### Post by fmbugdadi on 2008-01-01
Thanks for the info about Filter Internet Nat Redirection. I think you are right about how the file sharing works. That was pretty clever of who ever designed p2p software, to turn an incoming operation to an outgoing, knowing, neither your firewall or your router would stop it.

---

