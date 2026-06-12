---
title: "Help!  Wireless networking!"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by albs on 2007-03-02
Hi everyone,

I've been trying for about 4 hours on this... but no luck.  Basically, I've decided to migrate my computer to Edubuntu from Windows.

I have a new wireless card, a Netcomm NP542.  It works with windows.

I can see an entry for it in Edubuntu's device manager, but can't select it in my networking manger.  There simply is no entry for wireless, just my on-board ethernet card.  I can't Add a new device either, despite the help reference saying I could.

Below is the output of a "lshw -C network" command - any solutions anyone?


  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@00:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:f0800000-f080ffff iomemory:f0000000-f000ffff irq:209

---

### Post by zvezdogled on 2007-03-02
huh 
what does it say if u write command "lspci" and "ifconfig"

---

### Post by albs on 2007-03-02
Here's the lspci:

0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

And here's the ifconfig... the wireless interface doesn't even show up...

downstairs@edubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:78:36:A2
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe78:36a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85679 errors:9 dropped:0 overruns:0 frame:14
          TX packets:61211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87442418 (83.3 MiB)  TX bytes:5712898 (5.4 MiB)
          Interrupt:201 Base address:0x9800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5676 (5.5 KiB)  TX bytes:5676 (5.5 KiB)

Thanks for your help mate!

---

### Post by zvezdogled on 2007-03-03
i ma sorry it lookes like i can not help u.

---

