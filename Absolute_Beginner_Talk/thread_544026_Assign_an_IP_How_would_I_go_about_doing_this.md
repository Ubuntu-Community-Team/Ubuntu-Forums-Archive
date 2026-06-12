---
title: "Assign an IP? How would I go about doing this?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-09-05
From what I've read, it sounds as though I need to set the ip to 192.168.1.*** (router address is 192.168.1.1), but this doesn't work.

Any specific thing I'm doing wrong? I have Xubuntu 7.04, and one of these laptops works fine, but when I plug the same modem and cable into the other, it doesn't connect to the web.

And with this one, it tries before it says "cannot find server", but the other one doesn't even seem to try. Just says that straight off.

ifconfig results in this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.***
netmask 255.255.255.0
gateway 192.168.1.1


on the functional computer. The dysfunctional computer is the exact same except the the "address" line has a different set of numbers at the end.

---

### Post by ARandomKid on 2007-09-05
Haha. I was hopeful and did a reboot.

Didn't work. ;_; Hopes were crushed.

I admit I would've felt stupid if it had.

---

### Post by lloyd_b on 2007-09-05
First off, you need to determine what connectivity (if any) you have.

First test - In a terminal window:
```
ping -c 5 192.168.1.1
```
If this succeeds, then you know that you are getting as far as your router. 

Second test - In a terminal window:
```
ping -c 5 72.14.253.104
```
(This is a google.com IP address).  If this suceeds, then you are in fact connected to the internet.

Third test - In a terminal window:
```
ping -c 5 www.google.com
```
If this fails while the other two succeed, then your problem is with DNS (Domain Name Services - the thing that looks up a name like "www.google.com" and determines what IP address it's at).

From your description, I suspect it's number 3.  In that case, you need to add one or more lines to the file "/etc/resolv.conf":
```
nameserver x.x.x.x
```
where "x.x.x.x" is the proper nameserver for your location (try "192.168.1.1" first - if that doesn't work, you'll have to ask your ISP what nameservers to use). Note that you'll need a "sudo" or "gksudo" in order to be able to edit that particular file (like you did with "/etc/network/interfaces").

If this doesn't resolve the problem, please post the output from the tests (if possible), the contents of the file "/etc/resolv.conf", and the result of typing "route -n" in a terminal window.

Lloyd B.

---

### Post by ravenwere on 2007-09-05
Is there any particular reason why you are running static ips. Usually the DHCP service runs on the router and automatically serves up your network configuration.

---

### Post by ARandomKid on 2007-09-05
1st test failed. Can't even get to my router. ;_;

Sad, really.

Nothing reached 192.168.1.1

Route -n:

Kernal IP routing table
Destination        Gateway        Genamsk        Flags  Metric  Ref      Use  Iface
192.168.1.0        0.0.0.0        255.255.255.0    U        0          0             0   eth0
169.254.0.0        0.0.0.0        255.255.0.0        U       1000     0             0   eth0
 0.0.0.0            192.168.1.1      0.0.0.0            UG     0          0             0   eth0

/etc/resolv.conf:

*Doesn't seem to exist...should it? I found this by finding the resolv.conf file that was on this computer (working one). I wrote in the same stuff.

Is there something off about the route -n data and what's in my interfaces file? It seems different...

---

### Post by ARandomKid on 2007-09-05
> **ravenwere said:**
> Is there any particular reason why you are running static ips. Usually the DHCP service runs on the router and automatically serves up your network configuration.

In my case, DHCP refuses to give me a working ip on both computers. The only way I can get this one working was by setting it to static. It's the same for the nonworking one as well, DHCP does't want to give me any offers.

NO DHCPOFFERS RECEIVED...something like that.

---

### Post by lloyd_b on 2007-09-05
> **ARandomKid said:**
> 1st test failed. Can't even get to my router. ;_;

Sad, really.

Nothing reached 192.168.1.1

Route -n:

Kernal IP routing table
Destination        Gateway        Genamsk        Flags  Metric  Ref      Use  Iface
192.168.1.0        0.0.0.0        255.255.255.0    U        0          0             0   eth0
169.254.0.0        0.0.0.0        255.255.0.0        U       1000     0             0   eth0
 0.0.0.0            192.168.1.1      0.0.0.0            UG     0          0             0   eth0

/etc/resolv.conf:

*Doesn't seem to exist...should it? I found this by finding the resolv.conf file that was on this computer (working one). I wrote in the same stuff.

Is there something off about the route -n data and what's in my interfaces file? It seems different...

I don't see anything in the routing info that doesn't look reasonable (I have no clue what that 169.254.0.0 route is for, but it wouldn't affect your being able to reach a router at 192.168.1.1).

So you don't even have a basic connection.  You mention that you "connect the same modem and cable" - what exactly is that "modem"?  DSL? Cable?

And you mention that these are laptops.  Are they the same type, or two different brands/models?  I'm assuming that the connection to the modem is via Ethernet.  If so, are you using an onboard ethernet port, something via USB, a PCMCIA card?

Sorry for all the questions, but without a better understanding of just how you're connecting and what you're connecting to, it's difficult to identify the problem.

Lloyd B.

---

### Post by ARandomKid on 2007-09-05
Same type. ONe is Pentium III and one is Pentium II, but I doubt that makes much of a difference.

They both use a Xircom RealPort Ethernet 10/100+Modem 56...

I'm guessing this is a PCMCIA card, as I had to install that package before I could connect to the internet.

Goes from there to a Linksys router. I'm assuming this is DSL, as I know we don't have Cable.

---

### Post by bigboy_pdb on 2007-09-06
I had a problem connecting a wired computer to my wireless router and I realized that it could be a problem with the number of connections that were allowed. I thought that one more connection should be allowed, but after changing the settings (and checking the information regarding what IP addresses had been assigned), I realized the last available connection was being used by our Wii.

You should check how many connections your router is allowing. If it is using the maximum number of connections then it will reject additional connections.

---

### Post by ARandomKid on 2007-09-06
It should allow 4, of which 3 are being usd at most. (wireless laptop, this one, and a desktop computer.

But if I'm wrong, how would I go about disabling this one? (I'm not planning to use it once I hook up the other one.

---

### Post by southernman on 2007-09-06
from the machine in quesiton what does ifconfig show?

Also, login to your router from a accessible box and check to see that the IP you assigned staticly, hasn't been leased out by dhcp.

Also check in your router that you have it enabled to act as a gateway, verses a router. It will still serve as a router with forwarding, filtering, and the like.

---

### Post by uputer on 2007-09-06
OP, can you connect without a router?   

What does 'ifconfig' give you?   I went through the pains of setting up a static ip.

---

### Post by bigboy_pdb on 2007-09-06
> **ARandomKid said:**
> 
It should allow 4, of which 3 are being usd at most. (wireless laptop, this one, and a desktop computer.


Do you have wireless encryption enabled or are you using a filter that only allows certain MAC addresses to connect? If you don't have encryption, someone else might be accessing your router (and you're also letting people see any private information that you're sending to your router from your laptop). There should be a place (such as a tab called "Status" or "Wireless Information" or something like that) where you can see who is connected to your router.

> **ARandomKid said:**
> 
But if I'm wrong, how would I go about disabling this one?


You could always increase the number of connections or disable the wireless connections (assuming that you're not using a wireless connection) to be sure that these aren't problems.

---

