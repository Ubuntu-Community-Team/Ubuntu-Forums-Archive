---
title: "comcast troubles"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by struess on 2007-05-18
the problem:

my roommate and i just got set up with comcast today, and -- simply -- i can't get onto the internet.  hardware-wise, we have the cable from the wall running to the comcast modem, and a linksys hub connected to the modem.  the ports on the hub all work fine... my roommate's vista box gets onto the internet without any problems (i'm using it right now), and i tested each of the hub ports with it, but i get no connection from my dapper drake box.  plugging my box directly into the modem yields no connection either.  comcast tech support "does not support linux", unfortunately (though i wonder how many of their systems are running it...), so i'm thinking this is just a software/settings problem on my side.  

upon opening a browser for the first time with this new connection, my roommate had to go through a registration process with comcast and download/install some program.  i tried copying the files to my computer and installing the program, but it freezes up upon running the install.exe.  no luck there.  i haven't yet checked if his vista and my ubuntu can share files.

the output from ifconfig (taken from my computer via flash drive) is this:

eth0      Link encap:Ethernet  HWaddr 00:30:1B:B0:FC:0B
          inet6 addr: fe80::230:1bff:feb0:fc0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1162791 (1.1 MiB)  TX bytes:35604 (34.7 KiB)
          Interrupt:185 Base address:0xe000


any light you all could shine on this would be much appreciated.  thanks :)

---

### Post by k33bz on 2007-05-18
each of the linux boxes i operated works well with comcast system. so you are right alot fo linux boxes are using comcast. However, I do know that when i was fixing a freinds computer and i went to hook it up to my cable modem, i couldnt get on. and she runs on comcast as well. her box at the time was a win2k. So it has nothing to do with a hardware issue. I think it might actually be that comcast sets up the modem for each computer specially. Cant say for sure though. I know comcast doesnt support private hubs or routers. 
the program your freind downloaded wont help you much anyway. I did a fresh install on my XP system, as well as on my Ubuntu with no problems connecting with out downloading or installing any software

---

### Post by wormser on 2007-05-18
It does not sound like it is on Comcast's end since you can get the Vista box online.  Are you using a hub or a router?  Comcast only sends you one IP address via DHCP.  So, it sounds like the Vista box got online first and grabbed the IP address.  A hub is a 'dumb' network device and is not going to send out IP addresses to every computer on your network.  You need a router to do this.

Here are some things you can try.  Check the IP address on the Vista box.  If is something other than 192.168.x.x then you are probably on a hub and getting the address from Comcast.  To test your Ubuntu box unplug the cable modem and turn of the computer.  Plug the modem back in then reboot the computer.  If it is a hub then your Vista box will not be able to connect now.  

Post the model of equipment and results.

---

### Post by Repent on 2007-05-18
^ Strange I have one Linux PC and two Windows PCs online now using Comcast with no problems what so ever.

---

### Post by wormser on 2007-05-18
> **Repent said:**
> ^ Strange I have one Linux PC and two Windows PCs online now using Comcast with no problems what so ever.

Do you have a router?

---

### Post by Icemanyurt on 2007-05-18
Unplug the modem and router from power

Wait several minutes

Have the modem connected to the WAN side of the router

Plug in the modem into power, let it boot fully 

Plug the router into power, and it should be happy

---

### Post by wormser on 2007-05-18
> **Icemanyurt said:**
> Unplug the modem and router from power

Wait several minutes

Have the modem connected to the WAN side of the router

Plug in the modem into power, let it boot fully 

Plug the router into power, and it should be happy

Yes, but if he needs a router to get all the PCs online.  The Comcast modem does not have a router in it.

---

### Post by Icemanyurt on 2007-05-18
> we have the cable from the wall running to the comcast modem, and a linksys hub connected to the modem

:)

---

### Post by struess on 2007-05-18
your hypothesis was correct wormser:  when i removed my roommate's computer from the hub (it is a linksys hub, btw, not a router), recycled its power, and rebooted my computer, then my roommate could no longer get online.  however, my computer could not get online either.  

this leads me to believe that comcast does give out only one IP, and the hub just passes it along to whoever grabs it first... and that there might just be something wrong with the settings on my computer (eth0 is active, and is using DHCP). sounds like i need to go buy a router :(

any other ideas?

---

### Post by wormser on 2007-05-18
>  we have the cable from the wall running to the comcast modem, and a linksys hub connected to the modem


> **Icemanyurt said:**
> :)

Exactly, no router.  A hub is not a router.

;)

---

### Post by wormser on 2007-05-18
> **struess said:**
> your hypothesis was correct wormser:  when i removed my roommate's computer from the hub (it is a linksys hub, btw, not a router), recycled its power, and rebooted my computer, then my roommate could no longer get online.  however, my computer could not get online either.  

this leads me to believe that comcast does give out only one IP, and the hub just passes it along to whoever grabs it first... and that there might just be something wrong with the settings on my computer (eth0 is active, and is using DHCP). sounds like i need to go buy a router :(

any other ideas?

You need to go out and buy a cheap home router.  Then everybody can get online and you will have a firewall to protect the network.

You should be able to get online with your Ubuntu box.  Do an **ifconfig** to see of you got an ip address.  If not then **sudo dhclient eth0** tt obtain an IP address.  Eth0 is whatever you adapter name is.  If that does not work then I think you are screwed until you buy a router because you cannot manually set an IP address for Comcast.  So, the moral of the story is go and buy a router.

---

### Post by struess on 2007-05-18
so presumably, if i broke down and got a router, this is how it would pan out:  the cable modem would assign its single IP address to the router, which would distribute its own generated IPs to the devices plugged into it (by DHCP or by my specifying IPs, whatever).  

..and i wouldn't have to worry about installing any programs from comcast?

---

### Post by struess on 2007-05-18
right-o.  thanks a ton for your help.

---

### Post by wormser on 2007-05-18
> **struess said:**
> so presumably, if i broke down and got a router, this is how it would pan out:  the cable modem would assign its single IP address to the router, which would distribute its own generated IPs to the devices plugged into it (by DHCP or by my specifying IPs, whatever).  

..and i wouldn't have to worry about installing any programs from comcast?

Yes, that is right.  The router would give you 192.168.x.x private addresses to the computers on your network and get its IP from Comcast.  You can get routers for about $30.  Probably cheaper online from sites like shopping.com.

The Comcast program is just spyware type of junk.  They could use other methods to activate the account but choose to install junk on your windows box.  

Good Luck ;)

---

### Post by Icemanyurt on 2007-05-18
:p

Correct, 8/10 don't know the difference between a hub and a router so I made an assumption with those odds

---

### Post by Repent on 2007-05-18
> **wormser said:**
> Do you have a router?

Yes I run a Linksys Router and it runs perfectly. My bad I should have read your post a little better sorry.

---

### Post by wormser on 2007-05-18
> **Repent said:**
> Yes I run a Linksys Router and it runs perfectly. My bad I should have read your post a little better sorry.

No problem.  

> **Icemanyurt said:**
> :p

Correct, 8/10 don't knowo the difference between a hub and a router so I made an assumption with those odds

Yeah, a lot of people do not know the difference between a router and hub.  Remember what they say about to  ***-u-me.

Update:

It stared the first part of assume.  *** is not a bad word unless you are calling somebody that.

---

### Post by struess on 2007-05-19
problem solved.

gotta d-link router for $50, used "sudo dhclient eth0" to lease a new IP, and... poof, i'm back online.  my roommate's computer, along with all of our gaming systems, are also fully functional.

thanks for all the help :)

---

