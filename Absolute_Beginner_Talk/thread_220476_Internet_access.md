---
title: "Internet access"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by daputerguy on 2006-07-21
I am building a new PC and cannot get on the net. I am new to Ubuntu but not to building or repairing PC's. 

Reference information:
Motherboard - MSI K8T Master2-FAR Dual Opteron
CPU - 2 Opteron 242's 1.6Ghz
RAM - 2gb Micron pc3200 REG
Hard Drives - hd1 40gb Hitachi SATA
              hd2 160gb Western Digital SATA
JustLink - DVD-RW
MicroAdvantage - CD-RW
Video - MSI RX9550 256mb AGP
ISP - BellSouth DSL Ultra

On a seperate PC, I downloaded Ubuntu, burnt a disk and installed the system on this setup (above description).No problems with install. Mozilla installed automatically. I have been using this browser for some time and will not willingly go back to IE. At this point I was pleased with my progress. But when I try to go on the net I can't. I am doing something wrong! I cannot even access my DSL modem with Mozilla. Any Suggestions will be greatly appreciated. 
BTW The LAN connection is onboard, not PCI.

---

### Post by wpshooter on 2006-07-21
Have you checked all of your BIOS parameter settings to make sure that the NIC support is ENABLED in BIOS ?

---

### Post by ubuntu-geek on 2006-07-21
You might also check to make sure your DSL modem is serving up DHCP correctly. Or if you specify an IP you'll need todo that.

If you do a "ifconfig" at a terminal prompt you should see an IP address assigned to your nic card (if using dhcp). You can post back the output of that command here and maybe we can help troubleshoot further.

---

### Post by daputerguy on 2006-07-21
After much searching,I finally opened a terminal:
Link encap: Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inen6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:85783 errors:0 dropped:0 overruns:0 frame:0
TX packets:85783 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
RX bytes:6352715(6.0MiB) TX bytes:6352715 (6.0 MiB)

I like the appearance of this system but I wonder how long it will take for me to adapt to the terminology? I still find myself looking for M$ apps. Is there an operations manual anywhere?

---

### Post by l4v4_f10w on 2006-07-21
the setting you posted are the loopback something used to check if anything is wrong with your network, what i think u shud have is something like "eth0" which shud be your NIC card and it shud have an ip address if not try this, again im assuming that you default card is "eth0".
try "sudo ifconfig eth0 up"
now try ifconfig and see if you got an ip assigned.
If you didnt receive an ip address then you shud go >System>Administration>Network
click on ur network card again default will be eth0 and chick properties and check that DHCP is selected again this is assuming that your ip automatically assigns an ip to you through their DHCP Server. That shud hopefully help you.

---

### Post by daputerguy on 2006-07-21
I went as you directed and am now sending this reply via my new PC!
The names and procedures are going to take some getting-used-to.
A downloadable operations manual would be a big help to me and, I'm sure, a lot of others. Thank you for your help!

---

### Post by zxee on 2006-07-21
> **daputerguy said:**
> I went as you directed and am now sending this reply via my new PC!
The names and procedures are going to take some getting-used-to.
A downloadable operations manual would be a big help to me and, I'm sure, a lot of others. Thank you for your help!

There is some learning/learning curve to using linux. 
Welcome, we all started at some point in time and we never stop learning.
Manuals in linux/unix are right at you finger tips. If, say, you wanted to know more about the command ifconfig 
just type man ifconfig. That works for all the commands on your system as long as the man program is installed. 
Commands are in /bin and /sbin.

---

