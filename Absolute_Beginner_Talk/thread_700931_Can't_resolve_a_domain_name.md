---
title: "Can't resolve a domain name"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Docfxit on 2008-02-18
I have a Ubuntu ver. 7.10 install that won't resolve domain names.

I can ping an IP address just fine.  I can download files with an IP address.
I can't ping a domain name.  FireFox won't go to a web site with a domain name.
Any other PC on the LAN can resolve a domain name.

I have my DNS servers in the network setup.

Why can't it resolve a DNS lookup?

Thank you,

Docfxit

---

### Post by ice60 on 2008-02-18
maybe you can try disabling IPv6 in firefox :confused: i looked it up and you type **about:config** in the address bar and toggle **network.dns.disableIPV6**

EDIT i just saw you said you can't ping a domain name so forget that! if you've got wireshark/tshark you can watch your DNS queries with this if you need it -
# tshark -n -i eth0 port 53

---

### Post by brettg on 2008-02-18
HINT: You don't provide enough basic info here which is why nobody has answered you yet. Try to provide extra detail before asking for help. Consider the following;

Has this worked in the past or is it a new install?

Can you ping your dns servers by ip address?

Do you use DHCP or static IP?

Are you connecting via a router/gateway?

Do you have other PCs (or a dual boot OS) that works ok using the same dns?

Have you tried alternative dns providers such as opendns.org?

---

### Post by bumanie on 2008-02-18
Your problem sounds very much like the ipv6 connection issue. The only way to resolve it, (if this is the problem) is to blacklist ipv6 or disable it in firefox

[U]Blaclist[ method/U]
> sudo gedit /etc/modprobe.d/blacklist
At the end of the list type
blacklist ipv6
Save and reboot.

_Firefox method_
In the address bar type about:config
In th filter type ipv6
Right click on the ipv6 and toggle 
Restart firefox.

---

