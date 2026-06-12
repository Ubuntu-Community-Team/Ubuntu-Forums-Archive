---
title: "Can't find private IP address"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by rlgoddard on 2006-06-15
Hi all,
 
I am a Linux newbie and I have just installed Ubuntu 6.06 a few days ago. It is happily dual-booting with WinXP. I've ran into a few problems partitioning the hard drive for dual booting, but I was able to figure that out on my own. However, this next problem is vexing me...
 
I have a wireless network setup with a Linksys WRT54G router on a cable broadband connection. There are two computers, both with Linksys WMP54G Wireless-G PCI adapter cards. The downstairs computer is WinMCE only (Media Center Edition). The upstairs computer is WinXP/Ubuntu 6.06. I can connect just fine to the internet using my wireless connection (right out of the box I must add..) but when accessing the wireless router to get a list of DHCP clients, I only see the private IP of the downstairs computer. I don't see the private IP address of the upstairs computer.
 
My question is: how can I find the private IP address in Ubuntu? I ask because I'd like to set up RDP sessions between the two computers. I am able to set that up successfully (again, right out of the box) with Ubuntu connecting to the downstairs computer using Terminal Services Client. But I can't connect the downstairs computer to Ubuntu because I don't know the private IP address of the upstairs computer.
 
Thanks for any help you may have for me! I am having a much better experiencing using Ubuntu than using SuSE 9.1 three years ago.
 
Take care,
Russ

---

### Post by rai4shu2 on 2006-06-15
Network Tools will show you this information (In the System/Admin application menu). If you prefer the terminal, you can type "ifconfig" and your IP will show up as "inet addr" from that.

---

### Post by rlgoddard on 2006-06-15
[QUOTE=rai4shu2]Network Tools will show you this information (In the System/Admin application menu). If you prefer the terminal, you can type "ifconfig" and your IP will show up as "inet addr" from that.[/QUOTE]
Thanks!  I looked there one night, but I was looking at the loopback interface, and neglected to change the interface type to "unknown ra0".  When I changed the interface to view to "unknown device (ra0)", I got the IP i needed.  Thanks for your help!

Take care,
Russ

---

### Post by u.b.u.n.t.u on 2006-06-15
```
ip route
```

---

