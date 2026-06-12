---
title: "aMule and Low-ID"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by janki on 2006-11-23
I'm using aMule 2.1.0 on Dapper. Everytime I connect to the servers I am assigned a Low-ID. In [http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#What_is_LowID_and_HighID?](http://www.amule.org/wiki/index.php/FAQ_eD2k-Kademlia#What_is_LowID_and_HighID?) it says that port 4662 TCP should be open. I have used the command:
**sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 4662 -j ACCEPT**

When I try to restart aMule now, I'm still assigned a Low-ID. Anyone know how  to fix this?

---

### Post by TigerWolf on 2006-11-23
How are you connected to the internet? If you have a router you might want to look at its config and open up the required ports.

---

### Post by Rodneyck on 2006-11-23
If you have a router, it assigns an IP address to your machine. If the IP address ends in "0", most P2P networks consider this a lowid. There should be an option within your router to refresh the IP address (router assigns a random, new one) and make sure it does not end in "0".  This method should correct the problem.

---

### Post by Rodneyck on 2006-11-29
Well now I jinxed myself. I was getting HighID and fast downloads on aMule, but just the other day that all changed. No matter what I do, and yes I have the required ports open on my router that match aMule, changed the IP address to not end in "0" and still nothing. I even refreshed the server lists. KED, or whatever it is called, is now firewalled, which is odd, but I can not get it to change. aMule uploads files, but I am getting very slow downloads, if any at all.

I went through the forums and it appears lots of people end up having this problem with amule which makes me think there is a bug somewhere. To bad, as I really liked the setup and interface.  Oh well, on to try another...

---

### Post by esaym on 2007-01-03
> **Rodneyck said:**
> Well now I jinxed myself. I was getting HighID and fast downloads on aMule, but just the other day that all changed. No matter what I do, and yes I have the required ports open on my router that match aMule, changed the IP address to not end in "0" and still nothing. I even refreshed the server lists. KED, or whatever it is called, is now firewalled, which is odd, but I can not get it to change. aMule uploads files, but I am getting very slow downloads, if any at all.

I went through the forums and it appears lots of people end up having this problem with amule which makes me think there is a bug somewhere. To bad, as I really liked the setup and interface.  Oh well, on to try another...

Same problem here.  Anyone find a way around this?

---

### Post by Rodneyck on 2007-01-03
> **esaym said:**
> Same problem here.  Anyone find a way around this?

Check your network settings. Not sure how you connect to the web. I connect through a router/hub and my problem was that my router (for some reason) automatically changed my local network IP address, so I had to change the IP address where I was opening ports for amule. It finally worked, although amule is still buggy. ](*,)

---

### Post by esaym on 2007-01-03
> **Rodneyck said:**
> Check your network settings. Not sure how you connect to the web. I connect through a router/hub and my problem was that my router (for some reason) automatically changed my local network IP address, so I had to change the IP address where I was opening ports for amule. It finally worked, although amule is still buggy. ](*,)
Yea I discovered that I couldn't have the same port forwarded to more then one ip address the hard way........


Thanks for trying to help though

---

### Post by Paul_world10 on 2007-01-04
I want to get laughed at but I wonder if the server might be using a sort of proxy

---

### Post by esaym on 2007-01-04
> **Paul_world10 said:**
> I want to get laughed at but I wonder if the server might be using a sort of proxy

No the problem was on my end and the way I had my ports forwarded

---

