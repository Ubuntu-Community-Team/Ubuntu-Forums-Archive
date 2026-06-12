---
title: "VirtualBox: Basic Networking (NAT)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by bob-aptllc on 2007-02-26
I am trying to use VirtualBox but so far I have had problem after problem. This post is about networking. My guest is W2K running on a Edgy host. My host connects to the Internet via a Linux router using a static IP address and static DNS. How should I configure my guest to connect? I tried doing nothing but there was no connection. I tried setting the IP and DNS in the Windows TCP/IP settings like one normally would. Still, there is no Internet connection. I've read VB's manual and the Ubuntu VirtualBox documentation, but there doesn't seem to be a simple explanation of how to set up NAT, or should it just work, although mine doesn't. I don't understand how to set up even a NAT in the VirtualBox software. Please help! :confused:

---

### Post by bob-aptllc on 2007-02-26
When I removed all LAN settings and set everything back to automatic, it connected to the Internet. It must use the host's settings for IP and DNS. I caused myself extra work by trying to set them manually.

---

