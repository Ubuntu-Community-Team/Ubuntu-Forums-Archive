---
title: "mac on linux and dhcp, no networking :("
date: 2006-06-27
forum: Apple PPC Users
---

### Post by T31 on 2006-06-27
Hi guys!

     I am trying to make mol works with networking but everytime I try to start /etc/init.d/dhcp  I got an error like this on the syslog
=====================================
Jun 27 15:27:16 t31 dhcpd: No subnet declaration for tun0 (0.0.0.0).
Jun 27 15:27:16 t31 dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Jun 27 15:27:16 t31 dhcpd: network segment to which interface tun0 is attached.
Jun 27 15:27:16 t31 dhcpd: exiting.
======================================

Up to this I should make a subnet declaration for tun0 in the /etc/dhcp.conf file

Here is were I am lost :(

the rest of the steps for install mol I did from this how to [https://help.ubuntu.com/community/MacOnLinuxHowto]("https://help.ubuntu.com/community/MacOnLinuxHowto")

Anyone with mol and networking working :/ Ive been googling but without success till now

Thx in advance for the help

---

### Post by onehotcutey on 2006-06-28
I didn't use DHCP, instead I manually entered the IP addres and it works great, DHCP didn't work is why.  You may want to try this.

---

### Post by T31 on 2006-06-29
My problem is that when I start mol and go to system preferences I only see the modem, I cant modify en3 because there is not en3 :P

and ifconfig while I run mol seems ok

tun0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.40.1  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::d415:e1ff:fe29:4ea9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:6 (6.0 b)

:confused:

---

### Post by onehotcutey on 2006-06-29
Did you install the MOL utilities in OS X?  They should have appeared as a disk image on your desktop when you first logged in?

---

### Post by T31 on 2006-07-05
Thx for the replies!

Now after install these utilities you told me I got this :P
/////////////////////////////////////////////////////////////////////////////////////////////////
>> MacOS X Boot Loader 0.9.70
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4330344 bytes)
>> Old mkext timestamp (or safe-boot)
>> Loading from /mol-blk@0/disk@0:0,\System\Library\
>> --> Boot loader failure: Out of memory
cleaning up...
Initializing IP Masquerading...done.
Restarting DNS forwarder and DHCP server: dnsmasq.
Terminating threads...
DONE
/////////////////////////////////////////////////////////////////////////////////////////////////


and I did increase the memory to 192 first and then to 256 with the same result 8-[

---

### Post by onehotcutey on 2006-07-05
ugh... I encountered this same problem.  Sorry I had forgotten about it.  I eventually had to up the memory to 512 ( I have 1 gig ) but there was something else I had to do with the configuration files. 

I'll take a look at it tonight or tomorrow and let you know what I did.

---

### Post by T31 on 2006-07-15
Now works :) more or less

As easy as give mol 384mb of memory

lol

Now I face the second problem I cant get it to recognise any usb device, including my usb logitech microphone for skype :P

And after some problems with video I got it back but without audio :PPP

And for any reason now the windows that mol uses is bigger, whole screen but the panels than before

:-k

---

