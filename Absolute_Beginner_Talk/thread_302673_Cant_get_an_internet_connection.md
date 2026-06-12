---
title: "Cant get an internet connection"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by raith94 on 2006-11-19
I have just installed xubuntu on an old laptop(Compaq Pressario 800) and it looks good in all respects apart from being able to connect to the internet. The message im getting is cannot conect to Access Concentrator.

Am i missing something obvious?

---

### Post by adwait on 2006-11-19
Access concentrator.....you are using PPPoE right? Have you configured the IP settings correctly? (ie: Static IP/ Dynamic with DHCP etc..)

---

### Post by raith94 on 2006-11-19
Ok here is some more info about my problem

Im using an ethernet connection which is working fine on one computer and was working ok with windows on the other

From the command ping [www.google.com](www.google.com)
i get unkown host [www.google.com](www.google.com)

From ifconfig 
i get  etho    Link encap:Ethernet HWaddr 00:40:DO:1E:D6:33
               inet6 addr: fe80::240:d0ff:fele:d633/64Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:2486 errors:0 dropped:0 overuns:0 frame:0 TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:156420(152.7 KiB) TX bytes:468(468.0 b)
Interrupt:11 Base address:0x4000


Any suggestions?

---

### Post by raith94 on 2006-11-19
Its set to be dynamic
DHCP

This is what i am using with my windows system

---

### Post by raith94 on 2006-11-19
Im still struggling does anyone have any ideas?

---

### Post by Scorpuk on 2006-11-19
Hmmm on mine I get inet addr, but I dont see it on yours:

eth0      Link encap:Ethernet  HWaddr 00:17:31:4B:8A:43  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe4b:8a43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3805666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3933054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:346688673 (330.6 MiB)  TX bytes:799563425 (762.5 MiB)
          Interrupt:225 Base address:0xa000 


Try disabling your eth0 and then re-enabling.


or


Can you try giving your machine a valid IP address, based on your other machine?

ie. if your other machine is 192.168.1.2 then use 192.168.1.3 etc.

Also ensure you have the correct submask: 192.168.x.y should be 255.255.255.0 and your gateway will be your routers IP address. Probably 192.168.1.1, unless you changed it.

If still nothing then make sure you delete everything and then reselect DHCP


Hope it works. :)

---

### Post by raith94 on 2006-11-19
Yhanks for the idea but i just tried that but still nothing!
is there a possibility linux wont recognise the modem or be using the wrong driver if so how can i check this?

---

### Post by Scorpuk on 2006-11-19
Not sure how else I can help, but maybe the make and model of your modem might let someone else help a bit more?

---

### Post by raith94 on 2006-11-19
RealTek  
 Model   RCM RTL8139C-1C328Q1  im fairly sure this is the modem

---

### Post by Scorpuk on 2006-11-19
Is this an external modem or an internal modem?


Had a look at [www.realtek.com.tw](www.realtek.com.tw) and could only find information on RTL8139C(L) or RTL8139C(L)+. Neither look as though they are for ADSL.


If its internal can you goto a terminal window and type

```
lspci
```

This will list all devices on the PCI bus.

If external was that number you gave on a sticker on the mdoem?

---

### Post by raith94 on 2006-11-19
Its internal

RTL-8139/8139C/8139+

---

### Post by Scorpuk on 2006-11-19
RTL-8139/8139C/8139+ is not a modem and is a plain ethernet controller for use with local Area Networks.


What exactly are you connecting your laptop to, to try and conenct to the internet?


1. Directly connecting the ethernet socket on your laptop to the phone socket?

2. Connecting the ethernet socket on your laptop to a box (router) that is connected to the phone socket?


If its option 2 what make an model is this box?


If its option 1 then how exactly is the other computer connected to the internet?

---

### Post by raith94 on 2006-11-19
Its option 1 and so i have to keep switching the connection!

It worked fine when i was running windows so i assumed i could try the same with xubuntu.

---

### Post by Scorpuk on 2006-11-19
When you had windows installed on the laptop did it use the dial-up adapter for internet, using a telephone number, username and password?


I can't get any information as to the specs of a Compaq Presario 800 as its so old. :(

---

### Post by raith94 on 2006-11-19
no it just plugged straight in and used a dynamic DHCP.No dial up was always on a ADSL line or using a wireless card. Its a real pain as i said at the start im sure im missing something obvious but dont know what!!

Thanks for all your help

---

### Post by Scorpuk on 2006-11-19
Wish I could have been a bit more help, but goodluck with your problem.

---

### Post by adwait on 2006-11-19
It seems your laptop can't get an IP address from the DHCP server, can you ping the DHCP server/router?

---

### Post by raith94 on 2006-11-19
im not sure how to do that?

---

### Post by raith94 on 2006-11-19
bump

---

