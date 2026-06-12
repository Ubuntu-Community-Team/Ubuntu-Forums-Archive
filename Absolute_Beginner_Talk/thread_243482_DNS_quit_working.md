---
title: "DNS quit working"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by wwuster on 2006-08-25
I have ubuntu and a winxp machine on my local network. These computers can communicate to each other and the windows machine can  access the internet using firefox. But after the last ubuntu update I did a couple of days ago I can't get firefox in ubuntu to access the internet. It seems like DNS has just quit working. I can ping yahoo.com if I use the absolute ip address. I haven't changed any network settings on the linux machine.

How can I find why DNS quit working (if that is the problem)?

thanks,
William

---

### Post by benfindlay on 2006-08-25
Try disabling IPv6

in firefox type about:config
and double click on the option saying "network.dns.disable.IPv6"
This should read "True"

The other thing you could try doing is manually specifying your DNS server in the Network config. Your DNS servr can be obtained from your router's control panel

---

### Post by wwuster on 2006-08-25
I tried disabling ipv6 in firefox, but that made no difference. I finally got it working again using the /system/administration/networking application from the menu. I changed the DNS address to 192.168.1.1. It has worked for 6 months with these two addresses listed:
24.197.96.16
24.197.96.15

It works now, but do you know why it suddenly quit working?

William

---

### Post by benfindlay on 2006-08-25
Not sure I'm afraid. But if it works, then I wouldn't worry about it! ;)

---

### Post by kaptainlange on 2006-08-25
Maybe your ISP changed the IP's of their DNS servers?  Couldn't say for sure since I don't know what the DNS server's are now but that would explain why the Windows Computer could access it if you didn't manually specify the DNS for that machine.

It would have been using 192.168.1.1 as your DNS, your router, which would pull the proper DNS when it obtained your WAN IP.

---

### Post by seshomaru samma on 2006-08-25
> **wwuster said:**
> I have ubuntu and a winxp machine on my local network. These computers can communicate to each other and the windows machine can  access the internet using firefox. But after the last ubuntu update I did a couple of days ago I can't get firefox in ubuntu to access the internet. It seems like DNS has just quit working. I can ping yahoo.com if I use the absolute ip address. I haven't changed any network settings on the linux machine.

How can I find why DNS quit working (if that is the problem)?

thanks,
William

William I had a similar problem before , can you post your /etc/resolv.conf ?

---

