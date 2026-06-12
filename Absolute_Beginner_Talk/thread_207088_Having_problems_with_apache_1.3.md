---
title: "Having problems with apache 1.3"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by addict3d on 2006-07-01
I cannot view the webserver page when i type my dynamic IP in my web browser like [http://my.dynamic.ip.addr](http://my.dynamic.ip.addr) .. all i get is my router's login page .. I even tried from another computer (a net cafe computer) .. still the same result.. I can see only my router login page
I ll tell the steps i followed ..
1.Installed apache via apt-get
2.modified user and group in /etc/apache/httpd.conf to my username and group
3.Forwarded port 80 on my router (I'm sure this works now, cuz port 80 shows as open in [http://canyouseeme.org](http://canyouseeme.org))

I can see the web server's page when i type localhost or my private LAN IP address (i.e) 192.x.x.x, but not if i type my dynamic address.. What mistake did i do ? Thanks a lot

---

### Post by Apple 101 on 2006-07-01
Port 80 may be set to forward data, but don't you still need to set DMZ for the web server computer?  Also, check the computer is not running some kind of firewall.

---

### Post by addict3d on 2006-07-01
[QUOTE=Apple 101] Also, check the computer is not running some kind of firewall.[/QUOTE]

I neither installed any firewall through apt-get nor configured iptables. Is ther any other firewall that comes in-built with ubuntu ?

[QUOTE=Apple 101]Port 80 may be set to forward data, but don't you still need to set DMZ for the web server computer? [/QUOTE]

Ok, but what IP do i enter in the DMZ host field ? My LAN IP or my dynamic IP ? 

Thanks a lot for the reply.

---

### Post by addict3d on 2006-07-01
Never mind, i figured it out .. And sorry for disturbing ya ppl with such a silly question :D .. The router's web interface which was running at port 80 got changed over to 8080 when i forwarded port 80 .. But, as far as any PC inside my LAN is concerned (as well as my own PC) , it can see only the router's web interface (wonder why) at port 80 .. The netcafe computer i tried my dynamic IP on was also on the same LAN as my PC was .. So naturally it could see only the web interface of the router.. Now, I accessed my dynamic IP using a free proxy, and can see the listing of my /var/www directory :-)

P.S : Mods, do you close threads which have served their purposes ? If so, close this one .. Its pretty useless IMHO :lol:

---

