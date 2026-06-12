---
title: "ping to other Ubuntu computers is so slow ..."
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-09
On my LAN, I have 2 Ubuntu PC's - Klaatu and Barada.  When I ping to the other Ubuntu PC, ping works but it is very very slow.  When I ping an XP PC on my LAN, ping response is very fast.  It is also very fast if I ping say [www.Google.com](www.Google.com).   Now, Klaatu is running Feisty Fawn and Barada is running the beta for the next release of Ubuntu.  

If I ping an Klaatu or Barada using an IP address, it is fast.  I thought about giving up on dynamic IP's and going with static IPs.

Anyone else noted slow ping response?

Carl

---

### Post by myk.dinis on 2007-10-09
Sounds like your router/switch isn't performing it's functions properly. Try adding klaatu and barado to each others host files. That way they'll know that their names are associated with those ip's I know it's a pain in the *ss but hey...sometimes things don't always run smoothly...I had a similar issue and it turned out to be my router...it was old and on it's last legs and I didn't know it until I started having incredibly long ping times within my own network...on the windows side it went smoothly because of netbios and such...but it still wasn't perfect...try swapping your router for a known good and see if that helps...

Myk

---

### Post by cwmoser on 2007-10-10
Thanks.  I went ahead and made entries in my /etc/hosts file and now pings respond promptly.  I know this is not an optimal solution as that I am using dynamic IP addresses but it works.

BTW, there was a post to install winbind  --  i.e. sudo apt-get install windbind.  That hosed up my Ubuntu and made everything run slower and caused my NXServer to fail.  I uninstalled winbind and got everything working again.

Carl

---

### Post by myk.dinis on 2007-10-10
Yeah, it's not the perfect solution but it'll help in the meantime...

If you're using desktops in a home environment you should use static ips to help eliminate unwanted "guests" on your network anyways. If you have a laptop attached to the network or other wireless devices that join and disengage randoml then I would assign them reserved addresses with mac filtering...DsLites or PSPs or a Wii or other wifi devices...

This will help with a lot of problems associated with mixed platform environments...but...you should still check your routers functionality...just in case...

DHCP is usefull in academic or business environments because machines are always coming and going, the ip pool is limited and it's easier to manage from an IT standpoint.  But for a home network...invest a little time now on infrastructure and that'll help smooth the path later on.

Cheers!
Myk

---

### Post by cwmoser on 2007-10-10
Regarding Static versus Dynamic IP addresses, I find that my VPN client will not work properly unless I use a dynamic IP address.  Have you observed that?

In any case, I can still make an entry in my /etc/hosts address because the "lease" on my dynamic address is such that it consistently returns me with the same IP anyway.

Carl

---

