---
title: "Major Problem with network and internet"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by SierraKilo on 2007-02-20
Hey guys, I got a major problem with ubunto 6.10 and network connections. concider me to be a total beginner as far as linux is concerned.
I've got a Linksys Router who is connecting me to my dsl-connection, dhcp is deactivated.
In my computer i've got a Asus P5N32-SLI Premium Motherboard working, which has 2 lan-ports onboard (both nvidia-chipset).
Now her comes the problem: I simply can't get a connection to the router. Since I wasn't sure if eth0 or eth1 was the right port, i tried it with both. I switched to 'static IP' entered 192.168.1.101 as IP, 255.255.255.0 as Subnet, 192.168.1.1 as Gateway & DNS. checked ifconfig to see if the IP is assigned correctly, which it is.
BUT I've no connection icon in the top right corner and I can't ping the router. I also tried switching on dhcp on the router, but ubuntu is unable to get a ip-adress from the router.
Since the same problem happened under opensuse, i tried ubuntu on my laptop (also wire-connected) and surprisingly it worked without any problems. 
I'm no expert, but could it be that ubuntu has problems communicating with nvidia-network-chipsets? I can't think of anything else, hope someone can help me.

Thanks.!

---

### Post by luke411 on 2007-02-20
Did you try to set up your static IP by turning on DHCP on your router, and using the router/gateway IP# as your DNS server? The other option you might try to take some of the possibilities out of the equation is to by-pass the router all together and just connect straight to the modem and see if it connects with automatic DHCP. That would at least tell you if it's a network problem or a hardware problem.

---

### Post by SierraKilo on 2007-02-20
> **luke411 said:**
> Did you try to set up your static IP by turning on DHCP on your router, and using the router/gateway IP# as your DNS server?
Yes, I tried that, same result as before...

> **luke411 said:**
> by-pass the router all together and just connect straight to the modem and see if it connects with automatic DHCP.
Looks as if it's really a hardware problem. Can't get any IP from the modem, and therefore sadly no inet-connection :( 

But never the less, thanks for the quick reply!

Is there any way to instal new drivers for the network-adaptors? if there exist different drivers...

---

### Post by luke411 on 2007-02-20
Okay,
From what I can find, you have a very common problem with that chipset. It looks like the NIC is sharing a IRQ and it appears to be a driver issue. There is a driver for you from the vendor 

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)

Also I think the same driver can be activated within the kernel by doing a rebuild but I think you'll find it a little easier to install the driver rather than recompile the kernel.

You can check your IRQ's by typing 
cat /proc/interrupts
as root and see if you can spot any obvious conflicts but the driver installation may take care of it for you.

Good luck.

Oh, there's a pretty lengthy discussion about it on the NVIDIA forums. I didn't have alot of time to look but there may be a solution posted there if the driver doesn't do it.

---

### Post by SierraKilo on 2007-02-21
okay, thanks alot...

---

### Post by luke411 on 2007-02-21
Oh, I forgot. It looks like some people found success with turning off thier APM and ACPI. Maybe that's what is sharing the IRQ? AT any rate, if it's a desktop you could probably live without those anyway.

---

