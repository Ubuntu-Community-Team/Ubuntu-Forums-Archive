---
title: "Server can't reach internet, but I can remote control it over the internet"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by CaptSpify on 2008-01-01
I have a weird issue that I couldn't find any posts for. I have a server that can connect to the internet. I can remote control it from any other computer outside of my network, no problem. I have a problem when I try to go to a website and it wont connect. I try to run sudo apt-get update and it can't reach any server. I can't even ping any websites like Yahoo, but I can remote control it no problem. 

Any help would be appreciated...  :)

P.S. I couldn't find any other posts with this problem. If this has already been addressed somewhere else, let me know.

---

### Post by MrFSL on 2008-01-01
Sounds like a dns issue.

Do this, post the output of:
```
cat /etc/resolv.conf
```

From the server try to ping a website:
```
ping www.google.com
```

Can it translate google to its IP?

If not can you ping IP addresses? From here google resolves to: 64.233.167.99 so try:
> ping 64.233.167.99

If the IP is successful but the URL isn't, you have to add your dns servers to /etc/resolv.conf

```
nameserver <your_nameserver_ip_address>
```
Obviously substitute above with your actual DNS IP.

Cheers.

---

### Post by rivalarrival on 2008-01-01
My first instinct is that you haven't configured a valid DNS server. to check this:
```
ping 64.233.169.103
```

If you get a reply, it means you ARE connected to the internet (which you knew) but you don't have a DNS server to translate domain names like [www.google.com](www.google.com) into ip addresses like 64.233.169.103. 

System>Administration>Network - there is a tab marked "DNS" - you'll need to insert a valid DNS server in this tab.

If you can't ping, your gateway may be misconfigured, although I think that would prevent you from being able to connect from the outside as well...

---

### Post by MrFSL on 2008-01-01
Is there an echo in here? ;)

---

### Post by CaptSpify on 2008-01-02
It has my Gateway (router) listed there. Is that what you mean by DNS Server? I'm using a DNS Service (DynDNS), so I don't have an actuall DNS Server.

BTW, Yes, I am able to ping the IP, but not [WWW.Google.Com](WWW.Google.Com)

---

### Post by MrFSL on 2008-01-03
> **CaptSpify said:**
> It has my Gateway (router) listed there. Is that what you mean by DNS Server? I'm using a DNS Service (DynDNS), so I don't have an actuall DNS Server.

BTW, Yes, I am able to ping the IP, but not [WWW.Google.Com](WWW.Google.Com)

DynDNS is so that others can find you - you need to find others. You need to tell your computer (and your router for that matter) what servers to go to to look up the names for other people. Your internet service provider should supply you with this server. If your other computer can ping by url then you can check its settings to get the correct DNS addresses. 

Please post the terminal output of:
```
cat /etc/resolv.conf
```

---

### Post by CaptSpify on 2008-01-07
search Woodard
nameserver 192.168.0.2

---

### Post by MrFSL on 2008-01-07
This seems to be a straight-forward dns issue. If 192.168.0.2 is the address of your home router, then I must assume that it isn't functioning correctly is terms of DNS. I would check the settings on the router and assure that it has properly received DNS address(s). I would then try to ping these DNS addresses to assure that they are reachable. 

After verifying that these DNS servers are reachable i suggest putting them in your /etc/resolv.conf file.

---

### Post by CaptSpify on 2008-01-08
But my router is functioning OK. Every other computer on my network can hit any website by name just fine, this is the only one with this problem.

---

### Post by CaptSpify on 2008-01-08
Awesome, I figured it out!

My DSL Modem is 192.168.0.1
My Router is 192.168.0.2

I entered both of those IP addresses as DNS Servers in the Ubuntu Network GUI, and it started working!

Thanks for your help!

---

