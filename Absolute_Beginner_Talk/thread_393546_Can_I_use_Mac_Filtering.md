---
title: "Can I use Mac Filtering?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by IronLike Monkey on 2007-03-25
I know absolutely nothing about Wifi and Linux.  Can I use MAC filtering on my router with Ubuntu?  How can I look up my Mac Address in Ubuntu?  Thanks.

---

### Post by chili555 on 2007-03-25
Certainly you can. You can find the MAC address of your relevant interface with ifconfig. In my case, I get something like this:```
chili@LAPTOP:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr **00:E2:F6:A9:5A:F6** 
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```The text in bold is the MAC address. My router's admin pages say: Enter MAC Address in this format: xxxxxxxxxxxx. YMMV.

---

### Post by IronLike Monkey on 2007-03-25
Thanks for the quick reply. Ifconfig, like Ipconfig in windows? Simplier then I thought it was going to be. Thanks again.

---

### Post by chili555 on 2007-03-25
Well, so much more. ifconfig actually allows you to config, not just view. Wireless uses it's brother, iwconfig. Open a terminal and type man ifconfig. Close with Shift+Q. Also see man iwconfig.

You can bend every aspect of your linux system to your bidding.

Wanna see what's going on deep within the kernel? Easy, download the source code and read it. Afterwards, write M$ and ask for the source code to Vista. Yeah, right!

---

