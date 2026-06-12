---
title: "DHCP settings during installation"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by stokerfed on 2006-09-18
I have VMware setup, and am trying to get Ubuntu LAMP Server up and running for a testing environment. My problem is that itst not detecting my network settings and I have to manually enter the DHCP and IP settings, which I'm not the most knowledgable about. 

I have my network settings as according to my router:
IP Subnet Mask: 255.255.255.0
Gateway IP Address: 192.168.10.1

For the IP address setting, what am I supposed to put? Same goes for Primary DNS, I'm very confused.

Does anyone have some knowledge of IP that could help me out? Thanks so much!

---

### Post by buffy^ on 2006-09-18
You can set your IP to anyting above 192.168.10.1 (192.168.10.2 would work) and anything below 192.168.10.255 as this is your broadcast address.

The default gateway will act as your DNS server so 192.168.10.1 should work fine and you dont need a second one.

---

### Post by Iowan on 2006-09-18
The DHCP setting (unless you meant DNS) would be an either/or... either select DHCP or set fixed address, netmask, etc.  For server, you'd either want fixed IP address - or set up the DHCP server to assign static DHCP lease to this machine.  Static address is easier short-term, static lease means address can be managed from DHCP server.

---

### Post by stokerfed on 2006-09-18
Well, my goal is this to maybe help clarify my problem.

This is going to be a LAMP server for a website I'm building.
I'm trying to set it up so that partners of mine can SSH into the box from outside my network for development. For now tho, I'm just trying to get this up and running.

I don't think from my network settings I'm connecting to the internet. Every time I try to install something, even doing sudo apt-get update says, "Temporary failure resolving 'security.ubuntu.com'" etc...

I'm used to CentOS so the commands are a little flustered to me in Ubuntu, but 've heard great things. Where should I start with testing the internet connection?

Thanks so much for the help, btw.

---

### Post by buffy^ on 2006-09-18
try ping 66.102.9.99

---

### Post by stokerfed on 2006-09-18
Oh I'm a dummie, I knew about ping.

I can't ping anything, something's definitely not set up right.

What else do you need to know. I can find out all my router IP stuff, and my host computer's IP address as well because this is on a virtual machine.

So, where to start... grrr

---

