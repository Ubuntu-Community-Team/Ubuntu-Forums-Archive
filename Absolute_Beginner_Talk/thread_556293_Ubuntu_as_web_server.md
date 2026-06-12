---
title: "Ubuntu as web server"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by mike_hall_uk@yahoo.com on 2007-09-21
Help! I have installed ubuntu 7 desktop on an old desktop (P3, 256mb, 15gb) which is connected into the house adsl hub and I want to do the following: -

Leave it in my office and connect to it remotely via internet and “host” by own web sites.

I have heard about various stuff like LAMP, DNS, port forwarding, FTP, etc but its all very confusing.

I have created a few web sites on my windows laptop for which I have to pay for hosting but I want to “upload” my sites to my ubuntu “web server” at home.

The web sites are very simple html text & pics and not too big at all. I know cheap hosting exisits but I hate paying for a host and this is a bit of personal challange.

Thus I want to know how I “setup” my ubuntu server to share my home dynamic IP address & update the name servers. I don’t want to buy a static IP address.

Do I need to install the server version? Does a simple (i.e. good GUI) web server package exist? 

I am looking for a simple (!) guide to point me in the right direction.

So assuming I get to grips with setting up my web server I would then need to get my current web sites off my current hosts (1&1 + another).

---

### Post by Arthur Archnix on 2007-09-21
Given your usage, I'd forgo running the latest and greatest (i.e., Feisty) and install install a 6.06 server. [Here's]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") a nice little guide to start, I'm sure others will have more suggestions for you so stay tuned.

Best,

Arthur

---

### Post by Judgegeo on 2007-09-21
As you're new to Ubuntu it might be a good idea to install the GUI.

```
sudo apt-get install ubuntu-desktop
```

If I'm correct.

---

### Post by tgalati4 on 2007-09-21
Log into your asdl modem (typically 192.168.1.1 or 192.168.0.1) and see what features are available.  You will need to port-forward port 80 to your local machine.  For example, if your web server is located at 192.168.1.114 then you set Port 80 to forward to 192.168.1.114.

I would recommend setting a static IP for your machine, because you don't want the IP to change if you lose power or reboot.  There are lots of tutorials on how to do this in the forums (search static IP).

Register a domain-name at dyndns.org and set your external IP to this address.  As it probably changes (most asdl's are dynamic IP's) you will have to update it every 35 days or use ddclient or your router (some routers have an update feature built-in.  I know that newer Netgear routers have it).

If your asdl modem lacks a firewall, port-forwarding, and dyndns.org updating, then it's time to purchase a wireless (or wired hub) that plugs into your asdl modem to share your internet connection inside the house and provide these 3 critical functions to operate a web-server.

Here's an example of serving music files on a machine with a local IP of 192.168.1.114 behind a firewall with Port 9000 forwarded using a domain name registered with dyndns.org.  I'm using a netgear wireless, 4-port hub behind an asdl modem.

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

---

### Post by hyper_ch on 2007-09-21
well, on your current websites, do you use any domain names you own?

---

