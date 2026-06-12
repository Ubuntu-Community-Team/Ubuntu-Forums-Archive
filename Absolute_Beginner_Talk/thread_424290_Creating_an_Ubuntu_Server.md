---
title: "Creating an Ubuntu Server"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by U2XS on 2007-04-26
I'm turning my computer into a server using Ubuntu Edgy 6.10, following ([This tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3")).  In one step I have to change the "/etc/network/interfaces" to reflect my own IP and not the example.  However I'm not sure what to do about the rest of those addresses.  Do I leave them as is?  Do I change them?

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

Also, I am working from behind a router and I understand that at somepoint I need to set up a port forwarder. Is it now?  Thanks

---

### Post by nfinitone on 2007-04-26
Hey,
To answer your question quickly:
If you're setting up a server, you should already know what the IP address, network mask, and gateway are set to. if you don't, you should really look up some tutorials explaning basic IP setups.
As for the "network" and "broadcast" sections. You should follow the same octets as your IP address, and leave the fourth as 0 for network, and 255 for broadcast.

For example:
address *aaa.bbb.ccc.ddd*
netmask 255.255.255.0
network *aaa.bbb.ccc.*0
broadcast *aaa.bbb.ccc.*255
gateway *aaa.bbb.ccc.*1


You didnt provide much information as to the function your server, and if it will connect outside of your LAN. I've used that tutorial you've mentioned, and I find it to be a little too advanced for my needs. It's really suited for a web server and I believe it will require a lot of babysitting once it's up and running

 I have a print and file server that provides music and movies across my local network (via NFS for my girlfriend's Mac and my LinuxBox, and Samba for my XP box and PocketPC), and provides network access to two printers. It works very well and I used [THIS TUTORIAL]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html"). You should try that if you're setting up a local server. Give me more info as to what you're plans are and I'll be glad to help!

---

### Post by jondecker76 on 2007-04-26
Nice link! I was looking for something like that

---

