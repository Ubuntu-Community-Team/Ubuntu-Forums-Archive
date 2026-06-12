---
title: "Wireless not working on Ubuntu 7.10"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by Hairball600 on 2008-01-02
First of all, I am a new Ubuntu user, and have been using a Mac all my short life. I just installed Ubuntu 7.10 on a Mac Mini 1.83 GHZ, 512 MB ram, with an Airport Extreme card. I select my network (called Bag End) from the menu bar and type in my password. the icon changes to show how much signal I'm getting. I then open Network tools and ping the routers IP address, which is successful. However, when I switch over to Firefox, it says it is not connected. I can't use Add/Remove programs either. Any suggestions?

Thanks!

---

### Post by cyberdork33 on 2008-01-02
if you can access the router, then it is probably a problem with the router connecting to the internet... can you confirm that?

---

### Post by Hairball600 on 2008-01-02
Nope. The OS X computer directly connected to the router via Ethernet works just fine.

---

### Post by Hairball600 on 2008-01-02
Anyone?:confused:

---

### Post by cyberdork33 on 2008-01-03
> **Hairball600 said:**
> Nope. The OS X computer directly connected to the router via Ethernet works just fine.well that doesn't rule out that the wifi is different...

It is either something in the router, or maybe the dns settings are messed up on your Ubuntu machine.

---

### Post by Hairball600 on 2008-01-03
Could you (please) tell me what they are suppose to be?:guitar:

---

### Post by cyberdork33 on 2008-01-03
> **Hairball600 said:**
> Could you (please) tell me what they are suppose to be?:guitar:
they are different for your individual internet connection... Here are some links that may be helpful:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/616092.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/616092.html)
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

These should be set automatically, but it seems that something is wrong. Can you use a wired connection on the Ubuntu machine and see if you have the same issue?

---

### Post by madsmaddad on 2008-01-03
Whenever I had this problem it was always the DNS settings that were giving the grief. I notice that My Firefox is set up for 'direct connection to the Internet', and that the DNS settings are applied in the Router.

---

### Post by Hairball600 on 2008-01-03
YESSSSSS!!!!!:lolflag::guitar: All I had to do was set the thing from "LoopBack" interface to "Unknown(wifi0)". Thanks very much for your help! Thanks to ya'll, I am now writing this from Ubuntu.:guitar:

---

### Post by cyberdork33 on 2008-01-03
> **Hairball600 said:**
> YESSSSSS!!!!!:lolflag::guitar: All I had to do was set the thing from "LoopBack" interface to "Unknown(wifi0)". Thanks very much for your help! Thanks to ya'll, I am now writing this from Ubuntu.:guitar:
What thing? 

It would be much more helpful to others with the same problem if you could be a little more descriptive (and mark the thread as solved).

---

### Post by Hairball600 on 2008-01-03
Alright, sent the last hour trying to get it to work, and even reinstalled it, and while it works on the CD, it won't work on the actual install. So, it is not solved.:(

---

### Post by Hairball600 on 2008-01-03
Alright, can't figure anything out, so I think I am going to give up on it until it gets support for Airport.

---

