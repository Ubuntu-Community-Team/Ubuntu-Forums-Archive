---
title: "troubled mind - security open ports"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-08-08
just  read  this  [post]("http://abhay-techzone.blogspot.com/2007/08/safeguarding-ubuntu.html")

i receive the same output when using nmap - 

is this an open port that can be access from the internet or is  this guy just paranoid


i tried [shields up]("https://www.grc.com/x/ne.dll?bh0bkyd2") - going from the comments on  that post- and i got everything stealth but  this?
"Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation."

eh?

---

### Post by henriette_holm on 2007-08-09
Hi.
Answering your first question I think the guy is just being paranoid. If you have everything "stealth" you're fine.

Re. the ping request this just means that people on the internet are able to see when your computer is online. If you install Firestarter (a firewall GUI) I think you can ask the firewall do deny ping request.

/Henriette

---

### Post by splintercellguy on 2007-08-09
If you are connected through a router, and the router isn't forwarding any ports to your machine, then your machine should be fine. If your machine is directly connected to the Internet, then Linux has iptables. Firestarter is a GUI to help you manage iptables, sudo apt-get install firestarter. And I find ShieldsUp! to be a bit of paranoia-fest :P.

---

### Post by silent1643 on 2007-08-09
yeah thats pretty much what i was thinking to :)

thanks guys

---

### Post by eentonig on 2007-08-09
they guy is stupid.

1. "127.0.0.1" is your loopback address. Anybody attacking that ip, will shoot in his own foot.
2. To find vulnerabilities, scan the external interfaces.
3. Try the same from the internet
4. Firestarter is NOT a FW. It's a gui to the build in FW, called IP-TABLES

---

### Post by addux on 2007-11-30
I found this link helpful, I'm not sure what the downfalls, if any, are by ignoring ping requests.  This link will help you on your way.

[http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/](http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/)

---

