---
title: "[SOLVED] No connections from and to server"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by burningbunny on 2007-07-22
Hi
Since I installed webmin on my server and tried to setup a firewall, I can't connect to and from it (ie no ping or traceroute). Pinging localhost works, but thats about it.
I've tried: flushing iptables and restarting the network

---

### Post by DBStevens on 2007-07-22
I probably have too many questions but here goes:

The server you tried setting up the firewall on is it the same one that you can ping as localhost?

If it is the sameone as described above how are you trying to access it?

Could you post the firewall rules as an attachment?

Which firewall system are you using?

---

### Post by burningbunny on 2007-07-22
New information: For some reason I can now make outbound connections from the server (wget, ping), but incoming connections still don't work. I know this sounds weird, maybe it has something to do with ESTABLISHED connections working?

Setup is as follows:

Internal Network  <-> Ubuntu Server (DHCP, ssh) <-> DSL modem (not a router, access over pppoe)

> **DBStevens said:**
> 
The server you tried setting up the firewall on is it the same one that you can ping as localhost?


yep

> **DBStevens said:**
> 
If it is the sameone as described above how are you trying to access it?


From another Ubuntu box, from OSX and from Windows over the ethernet. I tried:

-setting a static ip on the server (ifconfig eth0 -pointopoint "address") and static ips on the computers that try to access it (same subnet)

-unplugging the whole DSL modem part using the server as a DHCP host (strangely enough it receives DHCPDISCOVER stuff from the computers in our internal network and even leases addresses)

then I tried pinging, sshing, web serving (webmin), and nothing works.

> **DBStevens said:**
> 
Could you post the firewall rules as an attachment?


as i said, they're empty because i flushed them (iptables -F). ACCEPT is the default for incoming and outgoing if I do iptables -L. iptables -n also shows lots of incoming packets. Are there parts of iptables i don't clear with the --flush option?

> **DBStevens said:**
> 
Which firewall system are you using?

I used the "linux firewall" module from the webmin interface, i tried loading the rules it created too, but that was what broke everything in the first place.

---

### Post by DBStevens on 2007-07-22
While I poke around at what webmin is doing these days would you please do:

sudo /sbin/iptables -L -n

in a terminal and post the output.

Hopefully it shows:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by burningbunny on 2007-07-22
Yep, it does.

---

### Post by burningbunny on 2007-07-22
Argh... I found the problem-
When the DHCP server is running, it reassigns its own address somehow... doing ifconfig just after setting a static ip still shows the one I assigned.
Still - This is not the behavior I want, as the (internal network) server IP changes periodically this way. What do I do?

---

### Post by DBStevens on 2007-07-22
So you have a server that is setup like this:

internet address x

modem (cable, whatever)

router (maybe)

internal address y probably of the form 192.168.x.y (or maybe 10.x.y.z etc private net addys)

your server

And you wish to run a firewall on your server.

A couple of questions:

1: Does the modem / whatever / router  have its own firewall system a lot of them do?

2: What do you wish to block, I think this gets back to the question about the original rule set.

As for this not being the behavior you want, you have to understand that you'll have to live with the capabilities of the other network components or put your server outside (maybe in effect if your network allows) of the network.  

In short on the inside it looks like you get a dynamically assigned address.  This in and of itself shouldn't prevent you from constructing a firewall.  You just have to be careful not to block things that it would be normal to block if your server was directly net facing.

---

### Post by burningbunny on 2007-07-22
> **DBStevens said:**
> So you have a server that is setup like this:

internet address x

modem (cable, whatever)

router (maybe)

internal address y probably of the form 192.168.x.y (or maybe 10.x.y.z etc private net addys)

your server

And you wish to run a firewall on your server.


Exactly.


> **DBStevens said:**
> 
1: Does the modem / whatever / router  have its own firewall system a lot of them do?


nope, ever since we changed our provider we can only connect using ppoe through a "dumb" modem. The modem is rumored to have limited routing capacities, but has an altered firmware. Unfortunately, it's illegal to hack it...

I want the server to connect through pppoe (which it does, hooray), and then i want it to use dhcpserver to provide addresses to our internal network, removing the need for every computer on the inside to start a pppoe connection.


> **DBStevens said:**
> 
2: What do you wish to block, I think this gets back to the question about the original rule set.


Everything that's not an established connection from the inside. I was orignially (trying to) follow [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html) .

> **DBStevens said:**
> 
In short on the inside it looks like you get a dynamiclly assigned address.  This in and of itself shouldn't prevent you from constructin a firewall.  You just have to be careful not to block things that it would be normal to block if your server was directly net facing.

The weird thing is that dhcpserver is running on the server itself. Shouldn't there be something preventing the server from assigning addresses to itself? Is there something i dont get about dhcp?

---

### Post by DBStevens on 2007-07-22
I see, interesting so you want 

Internet x

Modem (dumb as a rock)

server (should start as Internet x)

acting as a router for 

user mach1 (addy 1)  user mach2  (addy 2)  user mach3 (addy 3)

I assume that you have some switches in there or a pile of ethernet cards whatever.

I've never run anything in that cofiguration.  It souldn't prevent what you want to do.  In fact if that modem has a static address it should be a breeze.  It think I'll stop looking at what webmin is doing and see what that dhcpserver has in the way of configuration options.

---

### Post by burningbunny on 2007-07-22
Now that I've got webmin running again I'll see what I can do and report back if I got anything running.
Thanks for the help so far!

---

### Post by DBStevens on 2007-07-22
You might want to look at this:

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-dhcp-configuring-server.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-dhcp-configuring-server.html)

Just below the red Starting and Stopping the Server line.

It talks about setting one interface up to act as a client to retrieve a lease for the computer and an other to provide leases to other machines.   If your server is always first after the modem and the modem's ip doesn't change then you should be able to fix that interface.

---

### Post by burningbunny on 2007-07-22
Thanks!

I've got everything working now,  solved the DHCP part by adding the server as a permanent "host" with a static ip in webmin. 

Got everything else working using the shoreline firewall and this tutorial [http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm) as well as your link.

By the way, one of the main problems was not having BIND installed on the server, which then magically made everything work.

---

