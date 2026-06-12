---
title: "DHCP cannot connect to network PC's"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by ushills on 2008-04-21
Hi, previouly I used a static IP based network for my 3 pc's, however, i cannot get static IP to work with Hardy and my cards.

I am now using dynamic IP,s with PC's call media, main and other.  How can I connect to each pc using SSH or VNC, using 

```
SSH media
```

does not work?

---

### Post by sdennie on 2008-04-21
1) What kinds of problems are you having setting up static IP's in Hardy?

2) Does your router support handing out static IP address via DHCP based on MAC address?  This is a really nice route to take if your router supports it.

---

### Post by ushills on 2008-04-21
With Guts I had to compile the serialmonkey drivers for my RT61 card and used static IP's.  With Hardy my cards work naively but when I use a manual connection and set up a static IP I get cannot connect to network.
If I ping media I get a response 192.168.18 but says cannot find network.

In response to 2 my router does not offer this but it would be good if it did!

---

### Post by sdennie on 2008-04-21
Are you sure that all your machines/router are on the same subnet and they all have the correct subnet mask?  Also, if you switch from static to dynamic IPs, you may have stale entries in your /etc/hosts file.  Posting the IP address and subnet mask of each of your machines may be useful.  I'm not a networking expert so I'm not sure how much more I can help.

---

