---
title: "ssh tunneling to make a virtual lan"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-14
What I would like to do is use 2 ubuntu boxes as routers on 2 lan networks, that have connections to the internet. and have them setup so that they apper as one big lan too any clent on the network and uses ssh to do this so that its all secure.

help :) thnks

PS sorry i don't think this is in the right area as it may be more advanced but i didnt know were to put it :(

and i will make a grafic of what i would like and add a link to it in a min

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-14
ok so here what it would look like from an addmin view but from the user it would just look like everybodys on the local net work
[http://picasaweb.google.com/jwm280/SomeStuff/photo#5155206579128847922](http://picasaweb.google.com/jwm280/SomeStuff/photo#5155206579128847922)

---

### Post by The Cog on 2008-01-14
There's not a lot of documentation out there on how to do this. Here are some I found:
[http://www.perturb.org/display/entry/770/](http://www.perturb.org/display/entry/770/)
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)
[http://charles.karney.info/tunnel/index.html](http://charles.karney.info/tunnel/index.html)
by googling "ssh vpn tunnel how".

You need to do all the commands as root. One page suggests using NAT to hide the remote addresses. This is perhaps a good idea because otherwise you would have to introduce new routes into the buildings routers which might be problematic.

If you mean this to be a long-term connection, I would suggest that openvpn might be a better solution. It is well documented, should be more reliable, and will perform better than an SSH tunnel.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-14
The main thing is that the client computers don't know that the computers on the other lan are not on theres and that no configuration happens on those computers
is this posible with openVPN

---

### Post by The Cog on 2008-01-14
Not really. If you want to hide the fact that computesr are on a remote LAN, you are really getting into two different issues.

Firstly, for the servers that the clients connect to there is an easy solution, which is NAT. The connections coming from the remote LAN are modified so they appear to all be coming from the VPN-terminating computer. This can be done by any VPN as the NAT is done by the PC not the VPN application. The first link I gave shows how to do this.

Secondly, if the clients are to be unaware that they are connecting to remote addresses, you have to get fancy. You have to do an impersonation of a local address and then forward the packets to the address that you know to be correct. You could either do port forwarding, where specific port numnbers get forwrded to specific remote machines. Or if there is only one remote address that the clients need to access, you could just translate every packet with the appropriate destination IP address. 

Either can be done by using the NAT capabilities of iptables, and using this approach any type of VPN would work.

SSH has an extra capability of listening on specific TCP ports and forwarding connections to specific remote destinations, without having to mess directly with NAT. I suppose I would call this doing a TCP relay or TCP proxy.

So maybe the first issue is to decide whether you need access to one or many machines, and what protocols or applications will use it. SSH TCP tunneling is definitely the easiest if al you want is occasional single TCP connections. Other VPN methodologies get more complicated but may be able to set up concurrent access to multiple servers, or multiple protocols.

For the fullest connectivity, you need to introduce remote routes into the router at each sire, or if there isn't one already, you need to configure the PCs to use the Ubuntu boxes as their default gateway (maybe just a configuration change on the DHCP server to do this).

So what is your requirement? One client to access multiple servers, multiple clients to access one server, or fully meshed multiple clients to multiple servers?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-14
well what i would really like to do is have an xbox 360 lan with a bunch of boxes at 2 (or more) different locations. Because xbox is from Microsoft and i am not a lawyer i figure if i dont do any revers engineering or modding to the xbox then they cant sue me  for getting it "online" with out xbox live

so i dont know how much you know about xbox 360 but i dont know too much... a freind of mine gave me this project.
But maybe i can find out more about how xbox lan works then figure out what i need to do

---

### Post by The Cog on 2008-01-15
Hmm. sadly, I know nothing about xbox networking. But if they expect to be on a LAN, you may need to use bridging instead of routing. This will definitely need OpenVPN rather than SSH tunneling. But bridging will definitely work. Performance might be your next problem - LAN based protocols might well be very delay sensitive.

But get advice from someone who knows about xbox networking. I'm not even certain that they use IP.

---

### Post by The Cog on 2008-01-16
'll bump this myself since I too am curious about this subject. Maybe it should go in the networking section though?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-16
so i found out that there is some software that does this already 
[http://www.answerbag.com/q_view/1247](http://www.answerbag.com/q_view/1247)
[http://www.xbconnect.com/index.php?topic=screen](http://www.xbconnect.com/index.php?topic=screen)
only for windows thought :(

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-19
bum

---

