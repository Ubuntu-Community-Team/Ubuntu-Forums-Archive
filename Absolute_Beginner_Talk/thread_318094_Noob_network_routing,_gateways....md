---
title: "Noob network routing, gateways..."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by kingdave9 on 2006-12-13
I've almost given up on this, but I'll post here and see what happens.

Basically I'm trying to play Network Games in Wine.

Specifically Age of Mythology and Warcraft 3.

Basically in Age of Mythology:

I have a router and two machines: Win & Ubuntu.

When I try to run multiplayer, in Ubuntu I can see the Multiplayer Game the Win bx is hosting, but when I try to connect it just times out.

When I try to host a multi. in Ubuntu the Win box sees nothing.

I notice my IP in AOM in Ubuntu is 255.255.255.255.


I did some research and apperntly there are two ways of fixing this:

(Warcraft 3 below = same issue)

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

"If you try to play using the Local Area Network option, and do not see a game hosted from your machine on another or vice versa, and you are in the same subnet, this is likely caused by not having a default gateway. The game relies on sending UDP packets to the broadcast address and Linux will not send them unless there is a default gateway or another rule to handle them. To fix it, there are two methods:

Add a default gateway.
- OR -
Route 255. 255. 255. 255 to your local network."

**So I tried to add a route:**

"route add -host 255.255.255.255 dev eth0"
[B]
It didn't let me: "SIOCADDRT: Operation not permitted."[/B]
[B]
So then I tried adding a default Gateway:[/B]

"sudo route add default gw 192.168.1.1"

**and I get: "SIOCADDRT: file exsists"**


Basically how do I route 255.255.255.255 or add a default gateway... I'm totally lost and hungry and confused!

Thanks!

Dave

---

### Post by steve.horsley on 2006-12-13
You can see your routing table in Linux just by using the command **route**. If there is a default route (and I guess there probably is) you will see it there.

255.255.255.255 is the local broadcast address - packets addressed to this address are actually a broadcast to all users on the network. This address is not valid as a host address, so there is something wrong here. I just tried a networking program under wine, and it adopted the same IP address as my Linux ethernet port.

---

### Post by kingdave9 on 2006-12-13
Hey, thanks for the reply.

I ran route, here's what I got:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.22.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.78.0    *               255.255.255.0   U     0      0        0 vmnet1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


I think your right, the problem is most likely with wine. It's starting to sound like playing a lan game (AOM, War3 etc..) doesn't work under wine yet.

With wine 0.9.26 my ip in AOM was 0.0.0.0, and under 0.9.27 it's: 255.255.255.255.... so it looks like they're working on it anyways...

Thanks again

Dave

---

### Post by steve.horsley on 2006-12-14
I don't thnk wine is your problem. The network program I ran was under wine-0.9.27, and it got an IP address just fine. And I have used other networing programs in wine too. Even IE is said to work in wine. So I think the problem is with your AOM installation. Not that I have any idea how to fix that, I'm afraid.

---

### Post by freebeer on 2006-12-14
> **kingdave9 said:**
> 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.22.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.78.0    *               255.255.255.0   U     0      0        0 vmnet1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0



Um... maybe I'm reading this wrong, but aren't all these addresses on different sub-nets?  With the gateway address of 192.168.1.1, shouldn't eth0 be 192.168.1.2 (or any non zero, non 255 number), vmnet8 should be 192.168.1.3 (for instance) and vmnet1 on 192.168.1.4 (for instance)?  In other words the first three sets should be 192.168.1. and the last (octet?) a **unique** non-zero, non-255 number?

---

### Post by Bobtheknight on 2006-12-14
I'll give my opinion, but as it's my first time trying to help... don't be mad if I get it wrong.  Also, I am not sure the solution to your problem, but I do know about background info about routing tables.

what you gave is a routing table and routing tables don't tell you what ip address are connected to what interface.  Instead it tells you if you're trying to get to a destination, what interface you should send your packet.  This is my routing table:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

So it says if it's sending to anyone one on subnet 192.168.2.0 (my local network) it doesn't need a gateway (router) so it'll just use local traffic method.  Otherwise (default), it sends it to my router with the ip address 192.168.2.1.  Eth0 is my first ethernet card (the network card)

It appears you're on subnet 192.168.1.0, and your default gateway is correctly set to 192.168.1.1 unless your router is not on address 192.168.1.1.

Destination:  where you wanna go
Gateway:  where to send the packet to to go to destination

You could set a route saying that if the destination is 255.255.255.255, send it to "IP of WINXP" Genmask in that case would be 255.255.255.255 (match all digits).  I dunno what flags do but since it's local traffic I suggest copying the local traffic flag "U" and copy the rest eth0.  

I dunno what vmnets are (virtual network?) but I'm reasonably certain eth0 is your first network card.

---

### Post by steve.horsley on 2006-12-15
Bobtheknight is right. The number in the routing table is the network number, not a specific host address (normally). Your routing table looks right, assuming the vmnet interfaces are correct. But I have no idea which IP address wine would adoopt if you have more than one network interface working. Actually, I suspect it will use whatever IP address the outgoing interface has, which of course depends on what destination IP address you try to talk to.

What are the vmnet insterfaces?

It might be useful to use wireshark (or ethereal if you are still on Dapper - the name changed) to look at the packets the game is sending and receiving.

---

