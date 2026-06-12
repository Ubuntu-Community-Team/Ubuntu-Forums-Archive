---
title: "Ubuntu Server Startup"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by BlackOpsAlpha on 2008-02-12
I live in a house with about 20 people and we have decided to start up an Ubuntu server. I have no idea where to begin. Right now we have a 4 mps DSL modem (hope to get 8 mps cable) with dynamic routing. I have a 1.7 GHz Pentium 4 computer that I want to make into a server. What I am looking for our server to do is act as a bandwidth distributor. Making all available bandwidth evenly distributed amongst the computers on the network. Also I want shared hard drive space to be available to all computers on the network. We have mostly PC and some apple users along with a few Linux users. I have lots of extra hard drives and a few older 1 GHz AMD computer. In the future I am considering building a cluster. So right now I have no idea to start since I’m new to this. What would be the best ways to start?

---

### Post by hyper_ch on 2008-02-12
(1) you'd nee two network cards
- one for connecting to your (cable)modem
- one for connecting to your router

(2) the server will need to act as DCHP/DNS server (well, dhcp is not necessary if all machine get a static IP)

(3) network sharing can be done with samba for the windows computers. Are the Macs OSX?


This one sort of looks like it does what you need:

[http://www.howtoforge.com/fileserver_with_sme_server7.1](http://www.howtoforge.com/fileserver_with_sme_server7.1)

Selecting "server and gateway"

---

### Post by BlackOpsAlpha on 2008-02-12
I got it to work but i couldn't use gateway and server just server only. But it is up and running currently. I still don't know how to limit bandwidth or how to use the server with apple users.

---

### Post by hyper_ch on 2008-02-13
Why do you want to throttle bandwidth to a fixed rate? Wouldn't it be better to impose QoS?

Saying first priority would be email, www
Second priority VOIP
Third priority FTP
Fourth priority filesharing

Or somehow else ordering all those services to priority. I mean if you have 4 users and only one is online, wouldn't it be better if that user then had all connection available?

---

### Post by BlackOpsAlpha on 2008-02-24
Yeah i need to have a priority. I have 30 people on the internet some try to do all their homework but get screwed by the 3 people playing wow or something like that.

---

