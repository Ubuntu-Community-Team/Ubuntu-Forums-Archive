---
title: "how setup router for torrent downloads"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-11-20
I'm running through a router. and when attempting to set up azureus I get stuck at the nat server port section.

I got a warning message that reads "if you have a router/firewall, please check that you have port 57050 UDP open. decentralized tracking requires this.

I ran the sudo iptables -L command and got this:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


What do I do now?
-THanks

---

### Post by podunk on 2006-11-20
I never could get Azureus much above 6 kb. I found Bit torrando much better, and Ktorrent even better. 

In order to set up my router I had to log into my router using a web browser.

I got my IP by typing
ifconfig

Then adjusted the last number to get to my router. For instance I have a Westel router, and the last number needs to be changed to 254 like so

xxx.xxx.x.254

Some routers are .1 some are .255

I hate to say read the manual to folks, but Westells website had very thorough documentation on configuring my router. Unless you post the name and model number and someone happens to read your post with the exact same router we'd be taking a shot in the dark.

FWIW, once I logged into my router there is a menu
Configure
Expert
Forwarding

---

### Post by Dr. Nick on 2006-11-20
If you have a router then I doubt iptables is blocking you off, you will need to login to the web management on your router to open the ports up, look for the terms "port fowarding" or something like "special applications" and you can configure it their. And remember with bit torrent your speed just depends on the amount of people downloading it.
 
I am behind a router and have no fowarding but can still download ubuntu torrents at near top speed of my connection

---

### Post by Stew2 on 2006-11-20
Here is an awesome site for helping set up [port forwarding]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm"). It got my Azurues running like a charm and tells you exactly what to do for your specific router. Just click on your router model and it walks you through it. Check it out :D .
Hope this helps.

Regards,
Stew2

P.S. I routinely get speeds of 50 to 150 kbs.

---

