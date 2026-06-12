---
title: "Looking for some Internet sharing setup advice"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Silvain on 2007-12-22
Hi, here is my potential situation, in my local area there is a wireless internet service provider setting up services, They are installing towers, etc. to provide signal reach.I'm in the process of doing searches and reading up on internet shares currently. But right now I am uncertain as to what kind of interface their system will provide, I talked with the company on the phone and she said that they will "hard wire" one machine. Wish I knew for sure, what that would entail. If that means they will put a pci slot card in or what? If I knew for sure what that phrase meant, then would be better able to check up on "sharing internet set-ups" for sure. 

I currently have a few laptops with wireless cards and some computers with windows, D.S.L. , Ubuntu  systems and a 5 port Ethernet hub. Have been trying to figure out what would be the best set-up,  cost vs performance. So  would like to share the internet with all  of the fore mentioned systems But this is hard task, due to my not knowing about how the "hard wire machine" thing will work. 

So I guess my question is. Can any of you who have this hard wired set-up share , some of their set-ups slash configurations here, Am looking for ideas or advices .
Thanks in advance.

Silvain

---

### Post by blueridgedog on 2007-12-22
"hard wired" in networking parlance is typically (always today?) ethernet.  In that case you will want one of your ubuntu boxes to have two Ethernet cards, preferably ubuntu server and a rudimentary iptables configuration that will enable NAT between the two NICs (once "inside" and one "outside").

That said, you really cant speculate until you see how the service is delivered.

---

