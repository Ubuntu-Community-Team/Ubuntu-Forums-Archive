---
title: "internet connection"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by sjakos on 2006-12-17
I have a Belkin Wireless G USB Network Adapter, on the box it says that it only works with Windows, but I installed Ubuntu yesterday and a friend of mine told me that probably someone at ubuntoforums could help me. Anyone?

grtz

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> I have a Belkin Wireless G USB Network Adapter, on the box it says that it only works with Windows, but I installed Ubuntu yesterday and a friend of mine told me that probably someone at ubuntoforums could help me. Anyone?

grtz

I have been using a Belkin Wireless G PCI adaptor with more than one box running Ubuntu with no problems (beyond the normal annoying signal drop off when someone uses the microwave next door). However, a USB one may be using a different chipset. 

Okay, I would first start by trying to plug it in and see what happens. After you plug it in, try running "ifconfig -a", and capturing the output, after plugging it in. If you are really lucky, you might find that it already has been identified as a network device and then you just need the network settings. My wi-fi card shows up as ra0, so yours may be similar.

Either way post the ifconfig output and lets go from there...

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> I have been using a Belkin Wireless G PCI adaptor with more than one box running Ubuntu with no problems (beyond the normal annoying signal drop off when someone uses the microwave next door). However, a USB one may be using a different chipset. 

Okay, I would first start by trying to plug it in and see what happens. After you plug it in, try running "ifconfig -a", and capturing the output, after plugging it in. If you are really lucky, you might find that it already has been identified as a network device and then you just need the network settings. My wi-fi card shows up as ra0, so yours may be similar.

Either way post the ifconfig output and lets go from there...

and how do I run "ifconfig -a"?

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> and how do I run "ifconfig -a"?

Sorry, good question.
You will need to start a terminal to do that. Click on Applications->Accessories->Terminal,
and then type "ifconfig -a" in the resulting terminal.

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> I have been using a Belkin Wireless G PCI adaptor with more than one box running Ubuntu with no problems (beyond the normal annoying signal drop off when someone uses the microwave next door). However, a USB one may be using a different chipset. 

Okay, I would first start by trying to plug it in and see what happens. After you plug it in, try running "ifconfig -a", and capturing the output, after plugging it in. If you are really lucky, you might find that it already has been identified as a network device and then you just need the network settings. My wi-fi card shows up as ra0, so yours may be similar.

Either way post the ifconfig output and lets go from there...

I don't understand a thing of what's on the screen if I run ifconfig -a...

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> I don't understand a thing of what's on the screen if I run ifconfig -a...

Okay, post it here, and I can at least dissect it. 

I am not sure if it will help you more, but you could try running System->Administration->Network Tools, and telling me what is listed in the "Network Device" drop down in the devices tab there.

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> Okay, post it here, and I can at least dissect it. 

I am not sure if it will help you more, but you could try running System->Administration->Network Tools, and telling me what is listed in the "Network Device" drop down in the devices tab there.

eth0
Link encap: Ethernet         HWaddr 00:13:8F:07:ED:FC
UP BROADCAST MULTICAST    MTU:1500    Metric:1
RX packets:0       error:0        dropped:0        overruns:0         frame:0
TX packets:0       error:0         dropped:0       overruns:0         carrier:0
collisions:0       txqueuelen:1000
RX bytes:0 (0.0b)        TX bytes:0 (0.0b)
Interrupt:193          Bade address: 0xd400

lo
Link encap: Local Loopback
inetaddr:127.0.0.1     Mask: 255.0.0.0
inet6addr:  ::1/128   Scope: Host
UP LOOBBACK RUNNING    MTU:16436      Metric:1
RX packets:34     error:0         dropped:0        overruns:0       frame:0
TX packets:34     error:0         dropped:0        overruns:0     carrier:0
collisions:0     txqueuelen:0
RX bytes:2468   (2.4KiB)           TX bytes:2468 (2.4Kib)

sit0
Link encap: IPv6-in-IPv4
NOARP     MTU:1480       Metric:1
RX packets:0        error:0         dropped:0         overruns:0         frame:0
TX packets:0        error:0         dropped:0         overruns:0         carrier:0
collisions:0    txqueuelen:0
RX bytes:0 (0.0 b)        TX bytes:0 (0.0 b)

wlan0
Link encap: Ethernet    HWaddr 00:11:50:C1:2C:F3
inet6addr: fe80::211:50ff:fecl:2cf3/64     Scope:Link
UP RUNNING MULTICAST   MTU:1500     Metric:1
RX packets:0       error:0           dropped:0        overruns:0         frame:0
TX packets:11      error:0          dropped:0         overruns:0        carrier:0
collisions:0      txqueuelen:0
RX bytes:0 (0.0 b)          TX bytes:2376 (2.3KiB)
Baseaddress:0xf000

wmaster0-00
Link encap:UNSPEC       HWaddr 00-11-50-C1-2C-F3-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST        MTU:1500         Metric:1
RX packets:0      error:0                 dropped:0       overruns:0       frame:0
TX packets:0      error:0             dropped:0        overruns:0          carrier:0
collisions:0     txqueuelen:1000
RX bytes:0 (0.0 b)       TX bytes:0 (0.0 b)
Base address:0xf000

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> 
wlan0
Link encap: Ethernet    HWaddr 00:11:50:C1:2C:F3
inet6addr: fe80::211:50ff:fecl:2cf3/64     Scope:Link
UP RUNNING MULTICAST   MTU:1500     Metric:1
RX packets:0       error:0           dropped:0        overruns:0         frame:0
TX packets:11      error:0          dropped:0         overruns:0        carrier:0
collisions:0      txqueuelen:0
RX bytes:0 (0.0 b)          TX bytes:2376 (2.3KiB)
Baseaddress:0xf000


That looks like a very likely candidate. Okay, do you have your wireless access details handy (dont need to give them to me, just type them in the right places)?

If you go to system->administration->networking, in the main list, there should be an entry for "Wireless connection", if you click on properties, you should be able to enter your SSID, and other network details here. Try applying that, and see if you are connected.

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> That looks like a very likely candidate. Okay, do you have your wireless access details handy (dont need to give them to me, just type them in the right places)?

If you go to system->administration->networking, in the main list, there should be an entry for "Wireless connection", if you click on properties, you should be able to enter your SSID, and other network details here. Try applying that, and see if you are connected.

nope... still not working...

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> nope... still not working...

Okay - did you see the "Wireless connection" listed in the settings box?

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> Okay - did you see the "Wireless connection" listed in the settings box?

yes

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> yes

Okay, and what do you see when you click the properties box for that?

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> Okay, and what do you see when you click the properties box for that?

that connection is not enabled, so I enable it, I fill in all the required information (password, ip-adress,...) and I apply the changes.

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> that connection is not enabled, so I enable it, I fill in all the required information (password, ip-adress,...) and I apply the changes.

Okay - I would probably suggest DHCP on wireless. Did you ensure you got the right SSID and security key?

It is starting to sound like you have the hardware sorted, and are now into the less pleasant bit of the actual networking configuration...

---

### Post by sjakos on 2006-12-17
> **dannystaple said:**
> Okay - I would probably suggest DHCP on wireless. Did you ensure you got the right SSID and security key?

It is starting to sound like you have the hardware sorted, and are now into the less pleasant bit of the actual networking configuration...

I've entered the key four times, and I also tried once DHCP... nothing... had the same kind of problem in windows by the way, and one day I probably accidently clicked on something and it worked...

---

### Post by dannystaple on 2006-12-17
> **sjakos said:**
> I've entered the key four times, and I also tried once DHCP... nothing... had the same kind of problem in windows by the way, and one day I probably accidently clicked on something and it worked...

Oh - I see. Wireless networking can be a pain like that.. Have you made sure you have selected the right kind of key? There is a hexadecimal, or ascii key. That is - if you generated your keys from a typed password, that would be the ascii one, if you have a bunch of digits and letters, that is a hexadecimal key.

Can I suggest trying out wifi-radar? It is in the repository, and you should be able to find it in synaptic. Installing it should list the nearby networks so you can at least see what is available.

---

