---
title: "cant connect through VT6102 ethernet card"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by karaju on 2008-04-04
Hello,
I am new to linux.  I have installed Ubuntu 7.10 recently dual booting with WinXP.  I have an internet connection provided by a local cable operator, which is working fine in WinXP, but is not working at all in in Ubuntu.

I tried different methods suggested in different fora, all without success.  I also approached my ISP people, but they pleaded ignorance about Linux in general and Ubuntu in particular.

I have the following information to give:
AMD 2400, 256MB Ram, 40GB HDD.
When I tried to configure through GUI ie through Network configuration-Static IP duly giving all the details as required, nothing happens.  When I tried different things suggested in help forums, it appears that my net work card is recognized as VT6102 [Rhine II].  

I have all the details like Static IP addres, subnet mask, gateway etc., given by ISP people.

Please help in very very basic things, step by step, to configure my network connection.

Thanks in advance.

---

### Post by mikeyphi on 2008-04-04
Your card is supported in Ubuntu.
Open System/Administration/Network
select 'Wired Connection' - check box to left; with Wired Connection highlighted select properties - at right, then deselect Roaming Mode; set configuration (top line) to Static IP address; then input the required data in the next 3 lines. Select OK, then Close.
Should work!!

---

### Post by karaju on 2008-04-05
Thanks for the reply.  The procedure you have suggested is already tried but it does not work.  Any other ideas?  Thanks

---

### Post by mikeyphi on 2008-04-05
> **karaju said:**
> Thanks for the reply.  The procedure you have suggested is already tried but it does not work.  Any other ideas?  Thanks

Could have a look at a couple of ideas!
First - Not familiar with your set-up, does your cable internet plug directly into your computer? No modem/router?

Second - Open a terminal and enter these 2 commands in turn:

lspci
ifconfig

Look for info on your ethernet, the first should confirm card type the second should give some details re connection.

Post info re the card.

---

### Post by karaju on 2008-04-05
Thanks again for the quick reply.  My computer is connected through a direct cable to the adaptor.  No router or modem.  This is the out put for the commands you have suggested:

raju@raju-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

raju@raju-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:85:93:0B:24  

          inet addr:10.10.45.116  Bcast:10.10.45.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe93:b24/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:119 errors:0 dropped:0 overruns:0 frame:0

          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:18449 (18.0 KB)  TX bytes:3385 (3.3 KB)

          Interrupt:18 Base address:0xe400 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:144 errors:0 dropped:0 overruns:0 frame:0

          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:10936 (10.6 KB)  TX bytes:10936 (10.6 KB)
raju@raju-desktop:~$ 

I thank you very much for your patient replies once again.

---

### Post by karaju on 2008-04-05
Mr Mike, after posting the output above, I see that my Static IP address and DNS addresses are now mentioned in the "inet ad".  I think there is some thing which needs some tweaking.  Please help me.

---

### Post by StOoZ on 2008-04-05
all I can say is that I have the same card, built-in my M/B:
> 00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

was auto-detected by ubuntu 7.10, and works flawlessly.

---

### Post by mikeyphi on 2008-04-05
From the data you posted - it looks as though you have a working connection!
What Internet have you tried?

Open a terminal and enter:   sudo aptitude update
look for error messages - if any

Do you need a special webpage to logon to your ISP?

Finally - do a reboot....it's sometimes needed after changing Network settings!!!

---

### Post by MrWylbur on 2008-04-26
I have the same issues with the VT6102 NIC.  I am installing Ubuntu 8.04, and the network card appears and looks like it is installed correctly.  The NIC does not receive a valid IP Address from the dhcp client.  I have tried the following boot options to resolve this:

added acpi=noirq to the boot command
added irqpoll to the boot command

I have read a lot of threads on this (all I could find) and this seems to be an item that was supposed to be resolved in 8.04.  

I tried installing 7.10 and then upgraded to 8.04 without result.  Then I installed 8.04 fresh, and still no joy.  

Thanks for any insight!

---

### Post by magicvince on 2008-04-29
I had installed Hardy on pc with VT6102 ethernet card.
I can give him a static ip working on local net but I'am unable to access to the whole internet. No external ip pingable.

I try to log with acpi=noirq irqpoll, 

but nothing new happen.

---

### Post by cabaro on 2008-04-30
Maybe disabling IPv6 might help:

[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

also can you print output from command
```
sudo cat /etc/network/interfaces
```

---

