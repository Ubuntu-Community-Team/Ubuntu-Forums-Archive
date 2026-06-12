---
title: "Getting online"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2006-07-27
I've just intalled Ubuntu 6.06 and am having trouble getting online. I assume you use the 'Connect to Server.' What information do we put in the following categories? I use Netvigator.com in Hong Kong; a broadband service. BTW, I can't expect too much help from them. I asked them about Linux and they said 'Don't. Use Windows or Mac.' 

Service Type 
Server:
Port:
Folder
Name to use for connection

Thanks in advance and sorry about the ignorance here.

---

### Post by philippe_carlo on 2006-07-27
Is it a direct internet connection (and, if so is is PPP/PPPOE?) or do you connect through a router?

---

### Post by rowanparker on 2006-07-27
"Connect to Server..." isn't what you want, that is for connecting to file servers/web servers/etc.

Do you use a modem or router?

Rowan.

---

### Post by Stephen_A on 2006-07-27
Thanks for your response. I should have put this information. It is a Netvigator.com broadband connection, a Point to Point Protocol over Ethernet (PPPoE). It is (to the best of my knowledge) a direct internet connection. 

In Netvigator Broadband Properties, Networking 'This connection using the following items'has the following boxes checked. 

   Internet protocol (TCP/IP)
   QoS Packet Scheduler

I hope this is the information you need.

---

### Post by nicoliza on 2007-05-09
hey stephen,

i just download ubuntu 7.04 and can't connect to the pccw. have u fixed the problem?

---

### Post by Stephen_A on 2007-05-09
Hi Nicoliza. 
I don't know about the new version of Ubuntu but what I did was to follow exactly the insructions on this link. 

[http://ubuntuforums.org/showthread.php?t=183062&highlight=Eazy+PPPoE](http://ubuntuforums.org/showthread.php?t=183062&highlight=Eazy+PPPoE)

Then I found that it connected with PCCW without any problems. I hope it works fo you. 


Stephen.

---

### Post by cyleung on 2007-05-09
You may follow this link:

    [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems)

and refer to the section on ADSL Connections - PPPoE Modems.

cyleung

---

### Post by zvacet on 2007-05-09
system>administration<network settings>select your modem>properties>select type of connection8dhcp,static)>chek upper left box>close>DNS tab>replace address you find there with your nameservers>close


```
sudo pppoeconf
```

---

### Post by Stephen_A on 2007-05-09
Thanks everyone. Those links look useful. I'll make a careful note of them. 

Stephen.

---

### Post by nicoliza on 2007-05-11
Thanks everyone!!! it is so much easier to receive local advice.

Followed the instruction and after certain attempts, I finally did it.  Thanks all once again.

---

