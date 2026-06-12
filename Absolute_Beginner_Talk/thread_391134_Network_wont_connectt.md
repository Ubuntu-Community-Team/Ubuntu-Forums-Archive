---
title: "Network wont connectt"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by zeroo on 2007-03-22
I have kubuntu on one of my computers.  I have a wired connection and use a static ip.  I've typed in all my static ip information but I still have no luck.
Any ideas why I do not have internet?

---

### Post by dhtseany on 2007-03-22
Did you set the default gateway as "eth0" or whatever your devices' name is?

Can you ping any other machines on your network?

---

### Post by zeroo on 2007-03-22
All my other computers work. I set my default Gatway to 192.168.1.1, i think that is correct.
Is there anything I'm doing wrong?

---

### Post by dhtseany on 2007-03-22
Assuming you are using an "at home" router/switch, the default gateway would be the IP addy of the router/switch. 

Under the first "page" you see are the two or three different devices (Like eth0, eth1). On the bottom of that page you'll see a drop down menu that says Default Gateway: _____________

[[IMG]http://img88.imageshack.us/img88/9748/screenshotqn3.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshotqn3.png)

Thats the page you should be seeing. Don't mind the fact mine are greyed ou and say "Not Configured"t; i'm using a different network mgt. tool than you. But you'll see at the bottom the drop down list i'm referring to. Make sure that is set to your wired device's name (most likely eth0)

Did that help?

---

### Post by zeroo on 2007-03-22
Yes it is t to ETh0.  Also my router switch's ip is 192.168.1.1, so im guessing thats the number to be used for my gateway.
Is there anything else you know to do to help I do not know why its not working.
Also what manager are you using?

---

### Post by dhtseany on 2007-03-22
Well if you can't ping your other computers then its a problem with:
A) Drivers
B) Physical Connection
C) Software Settings

But if you can ping your other computers then its a problem with:
A) Software Settings

I apologize that I can't give you a more detailed explaination simply because I'm not sitting there to see what exactly its doing. 

Go to a terminal prompt and type:
```
$ ifconfig
```

and insert in onto this page if possible,



I'm running a package called "network-manager" however I'm only using it for WPA-Key support. It's still in the beta stages so I wouldn't recommend it unless you A) need to store multiple WEP/WPA Keys or B) you need WPA-Key Access.

---

### Post by dhtseany on 2007-03-22
Also, what is the make/model of your NIC/Ethernet Card?

---

### Post by zeroo on 2007-03-22
**Here it is **


eth0      Link encap:Ethernet  HWaddr 00:14:85:28:1D:52
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe28:1d52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8619 (8.4 KiB)  TX bytes:4136 (4.0 KiB)
          Interrupt:50 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24920 (24.3 KiB)  TX bytes:24920 (24.3 KiB)

---

### Post by dhtseany on 2007-03-22
Ok now trying this:
```
$ ping 192.168.1.1
```

What is the output from that?

---

### Post by zeroo on 2007-03-22
it is pingable,  it says recieving 64 mb  It works. So what should i do?

---

### Post by Josey on 2007-03-22
menu - system - administration - network tools

use ping and ping your gateway. 192.168.1.1
if you see replies then try to ping ubuntuforums.org
if you get replies then the problem is with your web browser
ping around and see where you get snagged

---

### Post by HereInOz on 2007-03-22
Sounds like a DNS problem.  Open Networking, click on the DNS tab, and enter the DNS addresses provided by your ISP.

If you can ping an IP address but can't access a web site, it is almost guaranteed a DNS issue.

Try:
ping [www.google.com](www.google.com)

If that fails, then it is more than likely DNS related.

---

### Post by Josey on 2007-03-22
Are other computers that are hooked to the same router having any trouble with the internet?

---

### Post by zeroo on 2007-03-22
Wow thank-you.

Exactly, a Dns Problem.  I typed in my dns and I was in.


Thanks for everything and your time.

---

