---
title: "Etnernet NIC issue after server rebuild"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by aussiedaddy on 2008-04-01
The motherboard on my Ubuntu server (7.10) fried itself.  Couldn't get the exact same motherboard to replace it but did get same brand same basic chipset.  New motherboard is ASUS DSBV-DX.  This has a gigabit ethernet capable on-board NIC.  After replacing motherboard server fies up OK and I can login to it but ethernet connection functioneth not.

lspci -nn tells me that I have Intel Corporation 80003ES2LAN Gigabit Ehernet Controller (Copper) [8086:1096] (rev 01)

(Actually it tells me I have two of them)

Is this based on checking the hardware I now have, or what was found when Ubuntu was installed?  How can I reprobe for correct NIC drivers safely?  Or what should I do?

I have data available on this server that I need but without an ethernet connection I can't get to it.

(I did try using a USB thumb drive but I couldn't find where it mounted - certainly not as it does on the workstation edition)

Thanks for any help you can give me

---

### Post by RealPSL on 2008-04-01
The lspci information is current. I am not sure about this but I believe most of the intel gigabit cards should be covered by the e1000 driver. If you run "lsmod" do you get a listing for e1000?

I have an intel 100Mb card so my output looks like below when I run lsmod | grep e100

e100                   37644  0 
mii                     6528  1 e100

---

### Post by aussiedaddy on 2008-04-01
I ran lsmod | prep e100 and got:

e1000         126656  0

ifconfig only gives me the local loopback although /etc/network/interfaces is unchanged and specifies eth0 at a fixed address

was working perfectly until the motherboard fried itself (a bit half melted!)

---

### Post by aussiedaddy on 2008-04-02
I ran ifconfig -a

That listed eth2 and eth3 as well as eth0.  Seems that Linux is remembering the ethernet NICs that were on the old motherboard.

I'll try configuring eth2 in /etc/network/interfaces and see how I go and that might just fix things

---

### Post by aussiedaddy on 2008-04-02
That did the trick.  I would like to know how to reconfigure it to eth0, however.

---

