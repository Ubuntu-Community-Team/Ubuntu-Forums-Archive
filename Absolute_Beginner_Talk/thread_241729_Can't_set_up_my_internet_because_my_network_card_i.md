---
title: "Can't set up my internet because my network card isnt comming up"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by mspear on 2006-08-22
Hi, 
 I am a total noob at linux. I have ran the little driver checker thing that ubuntu uses but when it gets to the networking part of the program, it kinda just craps out and still asks about mouse detected and all i cna click is cancel. i think it is because i have an onboard nic. I have a mach speed motherboard K8M8M(S). If anyone has a mother board driver please let me know.

---

### Post by Original Brownster on 2006-08-23
Hi,

> **mspear said:**
> Hi, 
 I am a total noob at linux. I have ran the little driver checker thing that ubuntu uses but when it gets to the networking part of the program, it kinda just craps out and still asks about mouse detected and all i cna click is cancel. i think it is because i have an onboard nic. I have a mach speed motherboard K8M8M(S). If anyone has a mother board driver please let me know.

I don't think your chip is supported out of the box I'm afraid, 
you could try the rtl8139 driver (it's a long shot)

from a terminal window type 'sudo modprobe 8139too' which will attempt to load the driver for many realtek cards.

then try 'ifconfig eth0', if it detects eth0 as being present it worked, if not then my honest advice and the easiest route is to buy a cheap nic and plug it in, nearly all are supported but check before buying.

I did find the following on the realtek site, the driver is available but requires work and some experience to get it going, with your level of experience you might consider the easier option.

[realtek info]("http://www.realtek.com.tw/products/products1-2.aspx?modelid=2003044")

[driver download]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=rtl8100")


Hope this helps

---

