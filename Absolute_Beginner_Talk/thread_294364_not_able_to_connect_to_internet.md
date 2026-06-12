---
title: "not able to connect to internet"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by manishraichur on 2006-11-06
Hi all
I am new to Linux and also to Ubuntu.
Yesterday i installed Ubuntu on my laptop (no windoze as dual boot ,since i want to completely take the plunge in Linux ).

Everything went smooth,but i am having trouble connecting to the internet.
I have a Dell 600M with built in wireless card.I think it is a broadcom card.I am trying to connect my laptop wirelessly to the internet.

In windows there was an utility which showed me all the available wireless networks which i can connect to.How do i see that in Ubuntu?I looked everywhere but i didn't even show my wireless network anywhere.

TIA
Manish

---

### Post by lyceum on 2006-11-06
Thry this link, no promises, but it should get you going in the right direction

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by manishraichur on 2006-11-06
I am trying to follow the guide,but it assumes that you have to ahve a wired connection to the internet.

Any suggetions please

---

### Post by manishraichur on 2006-11-06
Please help me guys !!!!! i am about to give up

---

### Post by manishraichur on 2006-11-06
Anyone? !!!!!

---

### Post by Imsati on 2006-11-06
Try this perhaps:


[http://www.ubuntuforums.org/showthread.php?t=188775&highlight=600m+wireless+internet](http://www.ubuntuforums.org/showthread.php?t=188775&highlight=600m+wireless+internet)

---

### Post by turbojugend_gr on 2006-11-06
go to system>>>admin>>networking or sth, thre it shows up your connections, if you see a wireless connection configure it, if not your card wasn't detected at installation... I use cable routing so I can't know more details...sorry. I hope you  will get this solved.

---

### Post by jamesr on 2006-11-06
personally I would go to a console terminal window and type the following ```
sudo iwconfig -a
```. If you post the result ie the output we should be able to help.

---

### Post by lyceum on 2006-11-07
Because you have to download a few things to get started, I don't know how else you could get the items you need to set up your wireless. I would recommend going to someone's house with wired access to use the link I gave you.

---

### Post by manishraichur on 2006-11-07
Worked!!!I am surfing now !!!
Thanks a lot guys.You have been very helpful.
One more thing that was in the guide was this code.

sudo nano /etc/network/interfaces

Change this line
Quote:
iface eth1 inet dhcp  

to look like this

iface eth1 inet dhcp
	pre-up sudo iwconfig eth1 rate 11M

Does that make any difference?Cuz i notice my connection is a little slow.

---

### Post by lyceum on 2006-11-07
I doubt that it does, wifi is normally a little slower. Have fun surfing!

---

### Post by jamesr on 2006-11-07
Glad that you got working. The surfing speed should not be affected by the 11M setup. Most broadband is still only 5Mbps although faster is starting to become available at a reasonable cost. But I would agree with lyceum that wifi seems slower than a wired connection on the same PC.

---

### Post by manishraichur on 2006-11-08
HELP PLease !!!!!!!!! 
I lost the connection again and am not able to get it to work now.I installed Ubuntu again and followed the same procedure,but with no luck.I don't want to give up on Linux.
Is there any other option?
How abt i buy a new external Network wireless card?
which one would you guys suggest?

Tia
Manish

---

### Post by jamesr on 2006-11-08
"Don't Panic" to use a Dad's Army phrase :) 

Because it worked before we should be able to get it working again. Please post the output that I requested before. From a Terminal window```
sudo iwconfig 
```This checks if the NIC is getting an address.If no address or one not associated with your router try ```
sudo dhclient
``` again post output.


How do you connect to the internet ?

internet ===modem==router~~~PC
            cable          wireless
              or 
            ADSL

---

### Post by manishraichur on 2006-11-08
I will post the output once i get home in the evening.
I connect through wireless with the card inbuilt in my desktop.

its the dreaded Broadcom 4306 chipset in Dell 600m

Thanks a lot for your replies.

Manish

---

### Post by lyceum on 2006-11-08
I had to get an external wireless to get mine to work. I am not very happy with Broadcom. Even if you get it to work, I find it too buggy. There is a list of ones that work at the FSF website

[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by manishraichur on 2006-11-08
i purchased a Belkin wireless card and installed the drivers..

Here is the output of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:CA:C3:96
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6596 (6.4 KiB)  TX bytes:6596 (6.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:D9:5B:1E
          inet6 addr: fe80::211:50ff:fed9:5b1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3006 (2.9 KiB)  TX bytes:3060 (2.9 KiB)
          Interrupt:11 Memory:f6000000-f6010000

manishreena@laptop:~/test$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

 Still not working

---

### Post by jamesr on 2006-11-08
It is not seeing any address, did you try? ```
sudo dhclient
```also ```
sudo iwconfig 
``` is better for wireless cards. It may be also useful to post the output of```
dmesg |grep wlan
```

---

### Post by manishraichur on 2006-11-09
Worked !!!!!!!!!! I am so glad that finally after 2 days i got it working.
I found out that Broadcom chipset in Dell 600m is very buggy even if you get it working.
My solution was ...i bought a external Belkin wireless card and used ndiswrapper to load the drivers.
everything is working now !!!!

Thanks a lot for all youe help guys.
you guys have been wonderful.

Manish

---

### Post by jamesr on 2006-11-10
Great to hear that the problem is solved but what actually fixed it was it just the change of the WNIC.

---

