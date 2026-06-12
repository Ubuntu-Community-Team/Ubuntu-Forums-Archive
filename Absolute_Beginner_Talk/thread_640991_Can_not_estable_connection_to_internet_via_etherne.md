---
title: "Can not estable connection to internet via ethernet"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by oilburner on 2007-12-14
Sorry to repost a question that has been asked dozens of times but thus far all solutions are failing. I just installed the 64bit ubuntu release on an HP (I know, shoot me) Pavilion dv2025nr notebook. So far everything has been runing fine with the exception of both wired and wireless internet. I have the wired connection set to automaticaly determan the IP adress. I use a direct connection to a cable modem. Any suggestions would be great. Thanks.

---

### Post by toddward on 2007-12-14
Could you do me a favor and show me the output of your ifconfig...


```

~$ ifconfig

```

---

### Post by oilburner on 2007-12-15
Sure, my output is as follows:


travis@Oil-Burner:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:05:2D:D7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I'm just missing the internet and also I need to get drivers for my music and usb sticks as well. I'm new to linux so I appologize. I'm just fed up to my *** with windows.

---

### Post by toddward on 2007-12-15
Ok, even though you set your ethernet device to be dhcp, it (for one reason or another) has not picked up on an address from the DHCP server.

Try running the following to restart your networking:
```

sudo /etc/init.d/network restart

```

It'll prompt you for the root password and will then go through and restart your network devices.

---

### Post by oilburner on 2007-12-15
I ran the command and the following is returned.

sudo: /etc/init.d/network: command not found

Is it posiable I had a faulty instal?

---

### Post by oilburner on 2007-12-15
Any ideas out there. Is there a way to use windows drivers? or, I'm lost, linux noob.

---

### Post by quinnten83 on 2007-12-15
you might want to read up on using ndiswrapper.But I believe that your wireless & network should be working.
Check which network cardyou have by typing 

```
lspci
```

and look for information about an ethernet controller.
I'm not so great with helping,but with the added info I sure someone else will be able to give a hand.

---

### Post by toddward on 2007-12-16
Really sorry about that...I work on multuple systems most of the time...sometimes screw up the commands.

It is actually:
```

sudo /etc/init.d/networking restart

```

---

