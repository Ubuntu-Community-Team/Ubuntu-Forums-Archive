---
title: "The mysterious case of the bipolar network drive"
date: 2011-04-13
forum: Any Other OS
---

### Post by Pureferret on 2011-04-13
Anyone following my posts here will know I've had some network issues. The on board one busted, and I've just gotten one, luckily from my dad. I booted up windows and it can't find a driver for it. I boot up Ubuntu, and I'm *straight* onto the web. Except I'd like to be able to use the internet on windows too.

So the driver exists on Ubuntu, and not on windows, and apparently not on the web either. Seriously, looked everywhere. All I can find are posts saying "Dude, where's my drivers?".

I'm cross posting this onto a windows forum, because that would make sense, but I was wondering if there was a way of porting it...or something? Clearly the Ubuntu drivers work.

This is the out put of lshw:
[CODE*-network
       description: Ethernet interface
       product: SC92031 PCI Fast Ethernet Adapter
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: eth1
       version: 01
       serial: [REMOVED]
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:fbfffc00-fbfffcff ioport:e800(size=256) memory:f0000000-f001ffff(prefetchable)

[/CODE]So where can I get windows drivers?

---

### Post by cubsfan53 on 2011-04-13
Try here.
[/URL][http://download.cnet.com/Silan-SC92031-PCI-Fast-Ethernet-Adapter/3000-2112_4-78610.html]("http://download.cnet.com/Silan-SC92031-PCI-Fast-Ethernet-Adapter/3000-2112_4-78610.html")

---

### Post by Pureferret on 2011-04-14
> **cubsfan53 said:**
> Try here.
[http://download.cnet.com/Silan-SC92031-PCI-Fast-Ethernet-Adapter/3000-2112_4-78610.html](http://download.cnet.com/Silan-SC92031-PCI-Fast-Ethernet-Adapter/3000-2112_4-78610.html)
That sends me here: [http://www.silan.com.cn/english/jszc/jszc.htm](http://www.silan.com.cn/english/jszc/jszc.htm)
Which is dead unfortunately. Same thing for the Zdnet link I was found....

---

### Post by fdm on 2011-04-14
I'm not 100% sure, but I think it uses the common Realtek RTL8139 chipset. If you provide the hardware id(ven and dev), the proper driver would be very easy to locate for you.

---

### Post by Pureferret on 2011-04-14
How would I go about finding the id(ven and dev) then?
 
(this is awesome by the way :D)

---

### Post by el_koraco on 2011-04-14
From what i can find on the web, you have to look for the Realtek 8139D ethernet controller.

---

### Post by fdm on 2011-04-15
Here is the terminal command for Debian(Ubuntu is Debian): 

lspci -nn | grep "Ethernet controller"

Here is a picture to show you how to do it in Windows.

[http://bayimg.com/EahicAAdJ](http://bayimg.com/EahicAAdJ)

---

### Post by mips on 2011-04-15
Realtek RTL8139 drivers:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=6&PFid=6&Level=5&Conn=4&DownTypeID=3&GetDown=false)




.

---

### Post by Pureferret on 2011-04-16
I couldn't get the driver to work, but for whatever reason I decided to try the old port. Low-and-behold it worked.

Thanks for all your help guys.

---

