---
title: "Can't get Xubuntu online Linksys router no server"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Ethan_Hunt_ph on 2007-10-26
Hello to the forum; I am in desperate need of assistance I am a new user and I could not get to network and connect to the internet  8 pcs which we reformatted and installed xubuntu 6.06 recently. 

We are running 8 pentium 3 733mhz w/ 128mb ram PCs.

The router is a Linksys WRT54G. No server we plug the router directly to a 24 port hub/switch.

Would appreciate your immediate assistance. Thank you.

---

### Post by Ethan_Hunt_ph on 2007-10-27
Guys if anyone is there please help we are doing this for a public school at a very poor neighborhood. Were trying to teach kids to use the internet. 

Would appreciate any assistance we already worked on the interfaces file and edited it accordingly. Still not connection. We would occassionaly get a connection but only up to the first web page (homepage) then we loose the connection for example homepage google would display then when we do a search we dont get anything. 

the pcs are connected to a router.

---

### Post by sad_iq on 2007-10-27
First you have to make sure the router can connect to the internet, get's an ip address, has all the dns entries correctly entered, and that the connection is stable. Then go to one computer and ping the router, then try to ping the internet(like google.com). Post your results here!!!

---

### Post by Boondock5 on 2007-10-27
I had similar problems with my linksys. I have the same model as your running now. 
If you don't get the encription levels to match on both router and computers, you won't get a connection. You will be able to see the signal getting to the computers but you won't be able to get online until they match.

---

### Post by CaptainInsaneO on 2007-10-27
You said the pc's are connected to a router, are they connected to the router you're using or do you have more than one router there?

If this is a broadband connection your setup should be something like this:

Internet>Modem>Router>Switch and then all your pc's should be hooked into the switch. All the pc's should have an IP address entered on the interface if you're not using DHCP.

I'm a netadmin so if you need further help with this, I'll be checking back.

---

### Post by lazyart on 2007-10-27
I would also connect a machine directly to the router and see if it can get online from there.  If so then the issue is the connection from the router to the hub.  Does the hub have a dedicated uplink port?  Is it a straight or crossover connection to the router?  Is there a button to toggle between the two?

---

### Post by Ethan_Hunt_ph on 2007-10-27
Thank you very much for your replies. We have the connections running we had the connections checked via a laptop and fluke tester (done by some of our volunteer) . Which eliminates any hardware problems.  We have online 1 windows PC working fine in the same switch/router LAN. BTW the router acts as our DHCP server. 

The modem > router > switch is a straight connection no crossover, no buttons to toggle this same network use to have windows units running without problems but those were pulled out and used by the school offices instead (they needed windows to run MS Office).

This LAN is used only for internet browsing and occasional open office. We already put in the correct DNS using network manager. 

I dont know how to go about matching the encryption of the router and the pcs. May I ask for assistance on how to do that.

when i ping the router the following are results

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data 

then nothing else


also the units were working fine on another network using identical router (this is were we installed it) also using same ISP so we find it really frustrating that the units would not run on the actual location when when we installed xubuntu in our offices it worked, when we deployed them it did not.

kids are already waiting we just have to defer next week till we get this done. 

Thanks a lot to all who replied. Will make sure to mention to the kids how this forum helped.

Thanks again.

---

### Post by Ethan_Hunt_ph on 2007-10-27
Sorry I was not that clear on the earlier post; the units connections are ok but the units still would not go online on the internet. 

so were still scouring the net for  possible solutions; we've tinkered with the interfaces file. the dns settings among others. still no luck. 

We tried using 1 of the units on a different network different still no luck.

BTW when we installed the Xubuntu 6.06 the autoconfiguration for networking failed several times so we opted to continue and manually just set. 

Thanks again.

---

### Post by CaptainInsaneO on 2007-10-28
Do you have DHCP running on your Ubuntu machines as well?

I know it sounds like a dumb question and I'm not trying to insult you. Sometimes though, the simplest things can cause the biggest headaches. :popcorn:

In terminal, do a```
sudo network-admin --configure=eth0
```

and make sure the config section says "Automatic Configuration".

Your cables, as you said, should be good. You want straight through on those connections.

Also, if you want (and if you trust me enough) I could take a look at your router from my machine and see if your configuration is good. I'd need the IP address though. If you want to try this method, just send me a private message.

---

### Post by sad_iq on 2007-10-28
Also...can you paste the result from **ifconfig** here??

---

### Post by Ethan_Hunt_ph on 2007-11-05
Sorry for late feedback we still have not resolved the problem, BTW, I dont take offense on any comments, I appreciate those of you who are direct and candid, it reminds us to check on things we may have missed. But no, the DHCP  configured and the router is actually configured as DHCP too, we have 2 windows 2000 running on this same router. 
I could not get back on the ifconfig since am not with the machines right now. Am at home. But I still would appreciate your help on this. Will try to copy the ifconfig results when we do this again tomorrow. Meantime, just so you know during our first install immediately after that we did get some of the machines to work for a short time. So its really bothering us why after a few pages of browsing we loose the connection. There really must be something wrong with the setup. 
Appreciate any assistance since its been some time and the kids are anxious of using the net. Otherwise we might as well revert the units to Windows98 (but I would rather have Xubuntu).
Thanks to sad_iq, captaininsane and the rest of you guys for the replies.

---

