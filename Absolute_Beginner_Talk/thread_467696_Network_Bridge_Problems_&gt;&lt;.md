---
title: "Network Bridge Problems &gt;&lt;"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by sraborg on 2007-06-08
Alright, I've been working on this issue all day, and I'm stumped. Here's what I'm trying to do.

I have a Router which is connected to my Computer (has 2 NICs running Ubuntu Fiesty) which is connected to my brother's computer (running Windows XP Pro). 

Currently, I am able to go online but my brother is not. What I'm trying to do is simply bridge the 2 NICs (eth0 and eth1) so my brother's computer is able to go online as well. Here's some relevant information.

Routers: 
        IP:192.168.10.1
        DHCP disabled. 

My Computer (eth0)
        IP:192.168.10.210
        Netmask:255.255.255.0
        Gateway:192.168.10.1

My brother's Comp
       IP:192.168.10.215
       Netmask:255.255.255.0
       Gateway:192.168.10.1

Keep in mind that these are all static settings (DHCP is not enabled on the router).

I've searched through several turorials and read several posts through the forum but no luck. I've also tried looking at the "man interfaces" pages but it wasn't much help to me.

So far, I've installed "bridge-utils" from the SPM, and I've messed with the /etc/network/interface file. Here's what it currently looks like.
> auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.10.210
netmask 255.255.255.0
gateway 192.168.10.1

auto eth1
iface eth1 inet dhcp

# [ a bridge which acts as an anonymous bridge ]
  iface br0 inet manual
     bridge-ifaces eth0 eth1
     up ifconfig $IFACE up
 
 # udev calls ifupdown for usb0 when it is created and destroyed.  See /etc/udev/rules.d/85-ifupdown.rules
 # Tell ifupdown not to assign an IP address and add it to the bridge.
 auto usb0
 iface usb0 inet manual
       up ifconfig $IFACE 0.0.0.0 up
       post-up brctl addif br0 usb0

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


auto eth0

I know it has to be some kind of minor setting that I'm over looking . It's been awhile, but I was able to get this to work quite easily when I was running XP on my computer; I can't imagine it being much harder to setup in Ubuntu.

Any and all help is appreciated.

---

### Post by matthewboh on 2007-06-08
Have you run brctl showstp br0?  Can you and post the results?

---

### Post by sraborg on 2007-06-08
Here are the results

> sean@Tank:~$ brctl showstp br0
br0: can't get info No such device
sean@Tank:~$ 


Please keep in mind, I'm familiar with networking; I'm just new to linux.

Just to try to clarify things; I'll try to re-describe the issue.

My computer has two Nic cards. The first card, eth0, is assigned the following settings: IP 192.168.10.210, Netmask 255.255.255.0, Gateway 192.168.10.1. My second NIC card, eth1, is hardwired to my brother's computer. My brother's NIC (on a Windows Machine) is assigned the following settings: IP 192.168.10.215, Netmask 255.255.255.0, Gateway 192.168.10.1. The router that my First NIC is hardwired to has DHCP disabled.

               [Router] <--> [(1st NIC) - My Comp - (2nd NIC)] <--> [Brother Comp]

How do I I bridge the two NICs?

---

### Post by matthewboh on 2007-06-09
At least we know it's not working.  Here's a link with step by step instructions on setting up several types of bridges

[http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html]("http://tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html")

---

### Post by sraborg on 2007-06-18
Sorry for the taking so long to reply. Well, I followed the tutorial on setting up a bridge. Using several sudo commands I was able to get the create the bridge and add NIC cards to it. From that point I get some interesting issues.

First off, I can only Ping with my LAN but not Ping out. Second off, if I reboot the computer, it deletes the bridge entirely.

I completely stumped...

:sad:

After working on this for so long, I'm just confusing myself. I remember setting up bridge in XP way back when and I don't remember them being this difficult.

Alright I'll recap again what I'm trying to do. I'm trying to let my brother comp (which is running XP) get internet access by go through my comp which is connect to a router. (Brother's comp) -- > (My Computer) -->(router). The router has an IP of 192.168.10.1.  What I would like is to have my brother's comp have an IP of 192.168.10.215 and my comp have an IP of 192.168.10.210.

Currently My Brothers Comp has the following Static settings made in Windows

IP:192.168.10.210
SM:255.255.255.0
DG:192.168.10.1

What do I need to do my comp which is running Fiesty?

I seem to be having two issues. 
Problem Number 1 is setting up the bridge correctly.
Problem Number 2 is after rebooting all networking changes seem to go out the window.

Please help me. I'm SOOOO LOST!!!!!!!!

---

### Post by HubertB on 2007-06-19
This is a workaround for this problem: Install ipmasq
```

sudo apt-get install ipmasq

```

Give your bros box and you second NIC an address of 172.23.15.1/24 (or any other private network, e. g. 10.10.10.1/24).

---

### Post by Austin_KW on 2007-06-19
This is easier to do using a routed/NAT solution. Install firestarter a GUI to iptables
sudo apt-get install firestarter

run the wizard in firestarter and share the internet connection, it will even allocate the local address to the second PC using a mini dhcp server.

You say you know networking, so I assume that for either bridging or NAT you are using a crossover cable as the PC nics will probably not do auto mdi-x

Why not just connect the second computer to the router?

---

