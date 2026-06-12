---
title: "network cable pc to pc not working"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-09-17
Hello,

I have two pc's which are both linux, they network to each other fine over the router I have but i really need to just network them straight together. This doesn't seem to work when they are connected via cable.

Note: They are on the same subnet

Anyone have any ideas on why it isn't working. the pcs cant ping each other.

Thanks

J

---

### Post by TLE on 2006-09-17
> **jd65pl said:**
> Hello,

I have two pc's which are both linux, they network to each other fine over the router I have but i really need to just network them straight together. This doesn't seem to work when they are connected via cable.

Note: They are on the same subnet

Anyone have any ideas on why it isn't working. the pcs cant ping each other.

Thanks

J

Well I'm no expert on network, but don't you need like a special cable to connect them directly, a "Cross-over"-cable or is that a thing of the past ?

---

### Post by christhemonkey on 2006-09-17
I believe you need to use/obtain a twisted end or cross over cable.

Although some NICs have some magic in them which means you dont need to bother, but i forget what its called....

---

### Post by buffy^ on 2006-09-17
TLE is quite right you want a Cross over clable also know as a patch cable. 

This cable looks almsot identical to a normal cable but it all boils down to the way in which its wired at either end.

If you visit a shop and ask for a patch cable they should know what you mean.

---

### Post by jd65pl on 2006-09-17
Yes i'm using a patch cable and have tried several different ones

---

### Post by buffy^ on 2006-09-17
OK when you plugg the cable into the network ports at the back are you able to see, the lights light up?

---

### Post by halitech on 2006-09-17
a patch cable is a standard cable for connecting a computer/device to a router or hub. if you are going from computer to computer then you need a cross over cable and yes, they do still make them. same basic price as a patch cable.

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

---

### Post by JayTee on 2006-09-17
> **TLE said:**
> Well I'm no expert on network, but don't you need like a special cable to connect them directly, a "Cross-over"-cable or is that a thing of the past ?

You definitely need what is called a Crossover cable, NOT a standard patch cable. Best Buy carries them and CompUSA if you live in the US and there's one near you. Make sure you specify to the salesperson that you want a crossover cable. The difference is that pins 1 and 2 are swapped respectively with pins 3 and 6 at the other end of the cable. This flips the send and recieve channels so that send on one pc is recieve on the other and vice versa.

---

### Post by Indras on 2006-09-17
Make sure you have a crossover cable.  You can tell right away by holding the two ends side by side.  If the color coding is identical, then it's a normal cable.  If one end is different (pins 1 and 3, and 2 and 6 should be reversed on one end, if I remember properly), then it's a crossover cable.  It should look something like this:
[http://www.inf.aber.ac.uk/stunet/images/setup/rj45cross1.gif](http://www.inf.aber.ac.uk/stunet/images/setup/rj45cross1.gif)

Basically, it just connecting the "send" wire to the "receive" wire on the other end, rather than straight through like you would to a router/switch/hub.

If your cable is correct and both cards light up (assuming they have lights, of course), then you need to make sure that either they have static IP addresses, or that one of the computers is running a DHCP server.  Most computers are set up to get their IP address from the first DHCP server it finds... if you have two computers connected directly together with no server, and they're both searching desperately for an IP address, you'll never get a proper connection.

I'd suggest setting a static IP on both of them, such as 192.168.0.1 and 192.168.0.2, and a sutable subnet mask: 255.255.255.0

Let me know if that works for you.

Edit: one more thing I forgot to mention, they also make crossover adapters, which you just plug into one end of the cable to convert it to a crossover cable.  Here's a picture of one:
[http://www.yourmobiledesk.com/images/productImages/ACF5627.gif](http://www.yourmobiledesk.com/images/productImages/ACF5627.gif)

---

### Post by jd65pl on 2006-09-17
Ok,

I am using a crossover cable. one of the pc's has a wireless connection to the router which is networked and working. When using nmap I can see the IP's but i they computers can't ping each other. ssh login works on localhost and the IP of the ssh server but other computer cant find the server.

edit:

IP address info

**PC number 1**
Wireless connection eth1
IP: 192.168.1.64
Subnet: 255.255.255.0

Wired connection eth0
IP: 192.168.0.2
Subnet: 255.255.254.0

**PC number 2**
Wired Connection eth0
IP: 192.168.0.1
Subnet: 255.255.254.0

PC 1 is my ssh client and internet connection access 
PC 2 is wired to my iternet connection and some external hard drives and is  a SSH server

---

### Post by Indras on 2006-09-17
It sounds like a routing/gateway problem.  PC number 1 has a default network connection (the wireless) and is using that connection's gateway address to route.  When you try to connect to PC 2, via 192.168.0.1, it makes a connection through the wireless connection and asks your wireless router to find the PC for you and forward the packet to it.  Since your router cannot see PC 2 via any method, it will never make a connection.

What you're going to need to do is set up some basic routing services on PC 1 and set it up to connect to 192.168.0.1 through eth0, and connect to everything else via eth1.  Here's a HOWTO I found on the subject:
[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)
Feel free to google for more if that one doesn't fit your needs.

---

