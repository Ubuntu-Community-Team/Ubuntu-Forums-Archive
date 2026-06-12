---
title: "What's the URL of my apache served pages?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by JMitchell on 2006-09-04
I've installed Ubuntu Server and set up a mediawiki page. I can find my page via the URL but is there a network name that would be easier to publish? I know my hostid but I'm not sure what to do with it...

That's the least of my problems at the moment as I'm trying to install RT and failing (See [this]("http://ubuntuforums.org/showthread.php?p=1461103#post1461103")) but this one feels like it should be easier to solve!

---

### Post by Jussi Kukkonen on 2006-09-04
> I can find my page via the URL but is there a network name that would be easier to publish? 
I assume you mean ip address and a http-url (www address)?

When urls are used, they need to be transformed into ip addresses. This can happen either on the clients (look at /etc/hosts) or using a domain name server.

---

### Post by Uluen on 2006-09-04
You probably know about [http://ip.to.your.server/](http://ip.to.your.server/) ? If you want something easier to remember for local webdevelopment, edit your /etc/hosts file ```
xxx.xxx.xxx.xxx yourservername
```

Then you can use [http://yourservername/](http://yourservername/)

---

### Post by gsdefender on 2006-09-04
> **Uluen said:**
> You probably know about [http://ip.to.your.server/](http://ip.to.your.server/) ? If you want something easier to remember for local webdevelopment, edit your /etc/hosts file ```
xxx.xxx.xxx.xxx yourservername
```

Then you can use [http://yourservername/](http://yourservername/)

Also remember that this method might work only from within your local system/LAN. If you need to be reached throughout the Internet, be sure to buy a domain name, or to use a dynamic DNS service like No-IP or DynDNS (both have GNU/Linux clients). You may also to need to change your firewall and NAT configuration.

---

### Post by JMitchell on 2006-09-04
Thanks for the replies - Jussi, you're right I meant I know the IP address and can navigate to the new site via that from the windows machines on the network, I just wondered if there was a url that would already be set up based on the hostname etc.

---

### Post by Bachstelze on 2006-09-04
Not unless you're running a DNS server and have registered a domain name. A free, hassle-less solution is to register a domain name from [www.no-ip.org](www.no-ip.org)

---

### Post by JMitchell on 2006-09-04
I don't need it available externally though, jsut on the network - I've not described what I want very well! Sorry!!!

---

### Post by Bachstelze on 2006-09-04
Oh, right. Then you need to edit /etc/hosts on each of your computers to specify the IP and the correct hostname for it, i.e., mine looks like :

```

127.0.0.1       localhost
192.168.1.1     livebox
192.168.1.2     miu
182.168.1.3     sakura
192.168.1.4     mika
192.168.1.5     aiko
192.168.1.6     sachiko

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

And it looks the same on every box on the network, so I can connect to all of them using only the hostname.

---

### Post by JMitchell on 2006-09-04
Thanks HTL - what about windows machines on the network?

---

### Post by argie on 2006-09-04
There's a hosts file on windows too.

C:\Windows\hosts

or wherever you installed windows.

---

### Post by Bachstelze on 2006-09-04
Actually, it's in C:\Windows\system32\drivers\etc :)

---

### Post by Uluen on 2006-09-04
The easiest thing would be setting up dnsmasq on one of your computers, it's a caching DNS and DHCP server.

---

