---
title: "setting my static IP from terminal ?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-29
how do i set my static IP up ? i am in command line mode - all documentation refers to doing via GUI.
does anyone know a good book from the terminal point of view -?
i want to set it to 192.168.5.2
which is the allocated IP on my router...

---

### Post by justleen on 2007-05-29
open the following file with your favorite editor /etc/network/interfaces :
```
sudo vi /etc/network/interfaces  
```

it will have 
```
 # The primary network interface
auto eth0
iface eth0 inet dhcp 
```

change is to 
```

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```
(change the IP's to your situation)

save and close

---

### Post by justleen on 2007-05-29
ohw, and restart the network afterwards with 
```
sudo ifdown eth0
sudo ifup eth0 
```

---

### Post by lupgop on 2007-05-29
thanks will try .....

---

### Post by esoterica on 2007-05-29
You need to also know and understand "DHCP"

It sounds like your trying to set up a static IP address on your computer in a DHCP environment where you have something like a router assigning the LAN IP addresses. Typically, there's a bit more to doing this than I think your expecting, it's easy, but the approach is different than what it sounds like your trying to do. It's pretty common these days that most people use a router for their internet connection that handles DHCP and assigns IP addresses to your individual computers. In many routers you can set static IP's for a particular computer on your LAN in it while stil maintaining dynamic IPs for other devices on your network. It may be doing this by MAC Address of the network card (either wired or wireless) or by computer name.

Since there are many ways and Linux utilities you could be using, and now that you know more about what specificly your looking for I'd suggest doing a google search for "Linux ifconfig to turn off DHCP" or similar to find instructions more specific to what your wanting to use to do this.

---

### Post by lupgop on 2007-05-29
can i ask the IPs ,,, my gateway will be
 192.168.5.1 Thats the router
guess my address is 192.168.5.2  ports 100 on are for dhcp)
what should go in network ???
broadcast ???

---

### Post by Docter on 2007-05-29
Device setup:

```
/etc/network/interfaces
```

Network script:

```
/etc/init.d/networking stop | start | restart
```

(The "|" means OR btw)

---

### Post by esoterica on 2007-05-29
All you need to change is the static IP your wanting to use, you need to make sure you tell your router your doing this though or it will not know and could assign the same IP to another device on your LAN. The other information like netmask etc... all remains the same as if your were using the dynamic or DHCP assigned Ip addresses, you don't need to change any of that to hold a static IP on your LAN, but you do need to let the device doing the IP assigning on your LAN what IP's to hold as static and not assign then to other devices.

The biggest problem you need to worry about is that you don't have more than one device on your LAN working as the DHCP server, this leads to some real weird problems you'll have a heck of a time figuring out how to solve or what the cause of it is. Typically you'll see this happen when a person is using a router connected to their Cable or DSL modem, and at the same time have inabled internet connection sharing on a local Windows computer (which puts it into DHCP server mode as well as your router which will by default act as a DHCP server). Router documentation is your best resource for getting the info your looking for, it will tell you how to assign static IP's to specifc devices on your LAN, doesn't really matter how or what you have the local computer configured to do, even configured to always obtain a new IP on the local computer as long as your DHCP server knows to always instead assign this device a particular IP by either MAC address or computer name it will, or at least should (like I said, strange things like other computers also running as DHCP servers on the same network can reek havoc on this).

---

### Post by wieman01 on 2007-05-29
> **lupgop said:**
> can i ask the IPs ,,, my gateway will be
 192.168.5.1 Thats the router
guess my address is 192.168.5.2  ports 100 on are for dhcp)
what should go in network ???
broadcast ???
Simply skip both network & broadcast. The system will set these automatically for you if you don't specify them. Don't worry.

_**EDIT:**_
Make sure you choose an IP address outside your DHCP range.

---

### Post by esoterica on 2007-05-29
weiman01,
I think what he's after is a way to place the IP in a DMZ or something so it's reserved as a publicly accessible server for either web or a game server maybe. At least this is the only reason I can think why you would specifically need to assign an IP to always be for a specific machine on your LAN.

---

### Post by wieman01 on 2007-05-29
> **esoterica said:**
> weiman01,
I think what he's after is a way to place the IP in a DMZ or something so it's reserved as a publicly accessible server for either web or a game server maybe. At least this is the only reason I can think why you would specifically need to assign an IP to always be for a specific machine on your LAN.
Could be, yes. You also need a static IP for file sharing between 2 computers in a local network. There are a number of reasons for it. DHCP is like a moving target. 

Let's see...

---

