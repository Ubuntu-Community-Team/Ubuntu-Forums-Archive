---
title: "how to connect to broadband"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by fahadrather on 2008-02-22
i am relatively new to broadband.....i need help to connect to internet using ZTE ZXDSL 831 AII modem...in ubuntu gutsy...i earlier used my mobile's gprs to connect..

---

### Post by webjames on 2008-02-22
Is that a USB modem?

---

### Post by fahadrather on 2008-02-22
usb as well as ethernet

---

### Post by ahsile on 2008-02-22
Which connection are you using? Ethernet or usb?

I've never had an issue with Ubuntu with an Ethernet connection before. Network-Manager just fires up the interface and it's all done.

---

### Post by fahadrather on 2008-02-22
i am using ethernet....i have not tried it on ubuntu thats why i am asking..

---

### Post by SunnyRabbiera on 2008-02-22
> **fahadrather said:**
> i am using ethernet....i have not tried it on ubuntu thats why i am asking..

It should work, ubuntu is usually good with this sort of thing...
I dont see why it wont work, most modems are generic.

---

### Post by ahsile on 2008-02-22
As long as your broadband provider is using DHCP there shouldn't be any issue. Network Manager will do everything you need automatically.

---

### Post by fahadrather on 2008-02-22
Nothing happens when i boot ubuntu.....there is a network icon on top which says wired network connection

---

### Post by webjames on 2008-02-22
that is correct, you have a wired connection to your modem via Ethernet cable. You should be able to browse the internet now and receive software updates for Ubuntu.

If you want more information about your connection right click on the network icon and select Connection Information.

---

### Post by fahadrather on 2008-02-22
No....i am not able to connect to the internet.....and i have to give a usr name and password....

---

### Post by webjames on 2008-02-22
okay, that normally is configured on your modem. please post the output of the following command when the modem is connected and powered on:

```
ifconfig -a
```

---

### Post by fahadrather on 2008-02-22
fahad@fahad-laptop:~$ ifconfig-a
bash: ifconfig-a: command not found
fahad@fahad-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:24:91:DD:8B  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe91:dd8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6418 (6.2 KB)  TX bytes:4931 (4.8 KB)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by webjames on 2008-02-22
sorry for the delayed reply.

okay, it looks like you're connected to the modem, but no to the internet yet obviously.
This means you need to activate your account.
This could be done in 1 of 2 ways:
1. If you start up your browser and type into the address bar:
> 
[http://192.168.1.1](http://192.168.1.1)


That should then load up the modem settings, you may be required to input a user name and password which you should have been given with your broadband documentation. Once you have logged into the modem it should be fairly straight forward to activate your account. I'm afraid i cannot provide any more information about this as each modem/supplier is different. However you should find information on this is the documentation package you received with the modem.
2. Some suppliers require you to go to a specific web page to activate your account before letting you browse the rest of the internet.

The good thing is that you are connected to your modem and ubuntu has done its bit. So it is now just a case of activating your internet, which your supplier should guide you through over the phone if needed.

hope this helps.

---

### Post by FreewheelinFrank on 2008-02-22
You'll need to configure your modem.

Enter the following in the address bar of your browser:

192.168.1.1

You will get the configuration screen for your modem. Enter your username and password.

Other settings as described here may be specific to your country and ISP.

Check with your ISP if you're still having problems.

[http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm](http://smartinfo.com.my/IT/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm)

---

### Post by maduranga on 2008-02-22
is it a router of a modem? if it is a router try to acces to the router page and do some modifications in settings. if you can't access the router page9 (192.168.1.1) then there maybe a problem with the network card that you are using to connect the modem/router. check if it works perfectly. try to configure DHCP. try to get help from the ISP or the modem manufacture.

---

### Post by fahadrather on 2008-02-22
The problem with the ISP here is that nobody uses ubuntu.....almost everyone is using windows...except me and few of my friends...therefore there is no real support ubuntu provided by the ISP....

---

### Post by FreewheelinFrank on 2008-02-23
The settings for your modem are not dependent on your OS.

Once you have accesses the router configuration screen, follow the instructions from your ISP.

---

