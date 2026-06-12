---
title: "Realtek Ethernet card"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Kanga on 2006-10-09
I'm new to Linux, having successfully installed Ubuntu on another hard drive on my computer. And with help from this forum ( thank god for it ), managed to get both xp and Ubuntu working with Ubuntu drive as master.
After reading the forums i've bought a Realtek ethernet pci card:
RTL 8139 Family PCI Fast Ethernet NIC.
It has been recognised by Ubuntu as: 0000:02:0b.ethernet controller unknown device 1904:2031 (rev 01)
I need help in getting it to work. I dont know if it will, should it ?
Please help if you can.
I'm almost going to sell it and buy a Netgear card, would that be a better buy ?:(

---

### Post by b_martinez on 2006-10-09
Yes it should work. The RealTek 8139,8139too,and 8139c drivers should be available to you. To find out if the driver is installed , in a terminal type

lsmod |less

and look for 'rtl8139'. It may have a 'c' or the word 'too'. If it's there, it's installed already.
 Under "System" go to "Administration" and then "Networking". Choose the "Ethernet connection", then"Properties"  and then 'Enable this connection".
If you got to this point, you should have the driver installed, already.
hth
Bill

---

### Post by Kanga on 2006-10-09
Thanks Bill, I tried : lsmod |less and found no rtl at all in the list.
Will I have to install the drivers now ?
Where from and how ? :confused:

---

### Post by Kanga on 2006-10-09
Another strange occurrence is that 'lspci'command in the terminal found that the ethernet card is mounted as an unknown device.
'sudo ppoeconf' commands' reply was "sorry no ethernet card could be found"
Is that because there's no drivers for it?
kanga.

---

### Post by Jason_25 on 2006-10-09
What is the output of 
```

ifconfig

```
?

That card should be supported out of the box.

---

### Post by Kanga on 2006-10-10
Here's the result for ifconfig :
Link encap:Local Loopback
inet addr: ::1/127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 Errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:272 (272.0 b)  TX bytes:272 (272.0b)

---

### Post by Kanga on 2006-10-10
Is it worth the bother ?
Would it be better for me to install another card which would be recognised, if someone could recommend one ?
Although through this forum's help there is a sense of satisfaction when things go right.
Help please !

---

### Post by Kanga on 2006-10-10
I'm having no responses, can't anybody help then ?

---

### Post by mips on 2006-10-10
Do a search in the networking forum for **8139** and you will find many posts on that chipset. If you have another card lying around try it.

---

### Post by mips on 2006-10-10
Try **modprobe 8139** might have to use sudo with that.

---

### Post by Kanga on 2006-10-10
Result in terminal for sudo modprobe 8139 is :
FATAL: module 8139 is not found
Thanks for replying - at my wits end.

---

### Post by mips on 2006-10-10
Have you done a search ?

I'm gonna sleep now.......

---

### Post by WhiteDawn on 2006-10-10
sorry about that....
if you cant get it working i would try ndiswrapper, but i would only use it as a last resort

---

### Post by Jason_25 on 2006-10-13
Please don't bother with ndiswrapper.  That card is supported out of the box and from your output it looks like it is working fine.  It just needs to be configured.

---

### Post by alsheron on 2006-10-27
I'm having serious issues too.... The problem is of course that i cant access the internet because my ethernet card will not work so i cant post ALL of the output of some commands at the terminal.

I'm pulling my hair out with this one...

I've tried all the advice here and on other forums and on other threads but my ethernet card isnot working.

Can someone do a step by step on how to make sure i'm trying to configure the right card and then how to enable it with thorough instructions please? I'm at my wits end and i don't want to have to change the network card because i know its not faulty....

---

### Post by Jason_25 on 2006-10-28
Is the graphical network admin tool not working correctly for you?

---

### Post by richardi on 2007-04-11
I too have the same problem. 
I recently installed dapper to dual boot with XP and would like to use it all the time but for no network connection. Triedand failed with exisiting USB modem and lots of mucking about with eciadsl. Then gave up and bought a Realtek RTL8139 Family PCI fast Ethernet NIC and a voyager 220V router adsl modem. Works out of the box with XP but not Ubuntu.
In the Graphical Networking config tool I just have a dialup modem listed - not configured and am stuck. Official Ubuntu book and Ubuntuguide are no help- any ideas for a total noob?
Thanks
Richard

---

