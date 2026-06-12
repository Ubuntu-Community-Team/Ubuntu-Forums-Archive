---
title: "Network question"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-06-18
A short while ago I asked a question about how to make bittorrent run faster. One of the replies I got was this

> all bittorrent traffic uses the port range 6881-6889. You need to:

a) Drop the routers firewall on those ports.
b) set up port forwarding to direct traffic on those ports to the internal mac/ip of your linux computer. Make sure you forward the entire range (6881-6889) on both TCP and UDP. 

My question is how do I do this? My router is installed on my dad's windows machine. Any help is greatly appreciated.

---

### Post by Nikusan on 2006-06-18
Your'e probably better off asking a question like this in a networking community.

Also try looking for portforwarding guides and things like that for your model router. Sites like homenethelp.com and azureuswiki.com/index.php/NAT_problem will help.

We need more information to help you like what model your router is, how your network is set up, etc.

---

### Post by keithjr on 2006-06-18
Most routers settings can be accessed by opening a web browser and entering the URL:  192.168.1.1 (although this varies depending on brand)

If you haven't set up a password yet, the default will still be loaded (it's highly recommended you change this if this is so!).  This default also depends on the make and model of the router.  Let us know what these are and we can help you more, and might even be able to direct you as to how to forward the desired ports to get rid of those nasty NAT problems.

---

### Post by TheFourElements on 2006-06-18
I have an SMC router model SMC7004VWBR. I don't have any of the packaging or manuals that came with it unfortunately.

---

### Post by uzi09 on 2006-06-18
try this site:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

---

