---
title: "Can't Connect to Wired Network"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-07
These threads are usually created because there are problems connecting to a wireless network, but in this case, it is a wired connection.

Anyway, I have an ethernet cable attached from my ADSL modem/router to my laptop and both of them (router and laptop) are recognizing it, evident by the lights. When I go to Administration > Network, I only have the Roaming and Modem options, but no Wired Connection options I saw in some screenshots. What do I do?

---

### Post by dsauxier on 2008-02-07
sometimes the acpi=noacpi boot option needs to be set to get wired nics working.
(some references say it should be acpi=off but I've used acpi=noacpi successfully in the past)

Before making changes to the grub menu PLEASE make a backup copy of it.
The file to edit is /boot/grub/menu.lst (make a backup of it right now)
Look for a section similar to (I've added acpi=noacpi) : 

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3423b914-8b51-492c-904c-33b8e09060d0 ro quiet **acpi=noacpi** splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

Other thoughts (if that doesn't help) : 

Do you also have a wireless card in the laptop?  
If so, please post the chipset if known.  What is the make and model?  Do you see any messages on boot regarding loading wireless drivers?  

It could be that the wireless driver is conflicting with the wired driver and needs to be blacklisted (or otherwise removed)...

Also, please run the following command in a terminal and post the output : 
ifconfig

If none of that helps, then hopefully someone else can help... that's about all I've got for wired nic troubles.

---

### Post by BLTicklemonster on 2008-02-07
I thought roaming mode *was* wired?

(if you need help with xp machines, there's a link in my sig that is the only way I've gotten it to work)

---

### Post by intense.ego on 2008-02-08
ifconfig gave me this
```
eth0      Link encap:Ethernet  HWaddr 00:13:02:52:A7:DE  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe52:a7de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9778 errors:10 dropped:5050 overruns:0 frame:0
          TX packets:8838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11178699 (10.6 MB)  TX bytes:1583765 (1.5 MB)
          Interrupt:21 Base address:0x6000 Memory:edf00000-edf00fff 

eth1      Link encap:Ethernet  HWaddr 00:16:41:56:18:9F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x3000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

My wireless card is an Intel PRO 3945. Just to clarify, I want to still be able to use wireless, but at times, I want to use wired because it will allow for faster speeds. 

Also, what command could I use for backing the grub file?

---

### Post by stchman on 2008-02-08
> **intense.ego said:**
> These threads are usually created because there are problems connecting to a wireless network, but in this case, it is a wired connection.

Anyway, I have an ethernet cable attached from my ADSL modem/router to my laptop and both of them (router and laptop) are recognizing it, evident by the lights. When I go to Administration > Network, I only have the Roaming and Modem options, but no Wired Connection options I saw in some screenshots. What do I do?

To get on to a DSL connection I thought you need to input a username and password.  Are those items stored in the router?

If yes, then is DHCP selected?

---

### Post by intense.ego on 2008-02-08
> **stchman said:**
> To get on to a DSL connection I thought you need to input a username and password.  Are those items stored in the router?

If yes, then is DHCP selected?

But how come the same doesn't have to be done with a windows pc?

---

### Post by dsauxier on 2008-02-08
To back up the menu.lst : 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig

I'm hoping that acpi=noacpi works, but if it does not, then you can try removing the wireless driver
(I understand that you want both working, but this is temporary - we need to at least test to see if the wireless driver is the problem)
first verify you have the expected module loaded : 
sudo modprobe -l | grep ipw3945

then remove it
sudo modprobe -r ipw3945

Or you can add it to the blacklist file so that it never comes up... that might be better as a test 
To do that, just add a line to the bottom of /etc/modprobe.d/blacklist : 
blacklist ipw3945
For this to take effect, you need to reboot.

To undo this, you just delete the line and then reboot.

---

