---
title: "general troubles with Edgy..."
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-03-11
Hi Guys.... been searching and reading for the following issues in my Edgy installation with no possible ways for me to exactly getting things done with Ubuntu.

here's the deal:

A while ago i used the live cd in winxp with vmware. I was just curious and after realizing that, probably, the one thing i could waste was time I installed it. When I was in windows the live cd (running it with vmware) could surf the net and i tried Gaim and Firefox just for playing. Got things right, it worked. Now that I installed Ubuntu when I log on there is no internet connection. I use two netword cards: the one that came in the board and a  Realtek RTL-8139. Both cards are recognized but there's no activity. Looked around if the realtek card (the internet one) had some trouble in ubuntu, but it doesn't. [Here's]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek")  it is listed as supported. But there are other people that have trouble with it. Looking here in the forums wasn't that helpful since some issues are fixed and others not. Don't know what's my case. In windows, running the live cd, checked for the cards installed and there's only one: the one vmware creates to use my (shared) internet connection.

Anyway, since this is the mayor problem i have with it some help would be fantastic. It's a real pain in  the *** log into the other OS, run the virtual machine and just look around how to configure the other one...


The board is a msi k8mm-v
Processor AMD sempron 2600 
Ram 1 Gb

Excuse my bad english....

Well.. sorry, again, for my n00bishness

---

### Post by pveith on 2007-03-11
Have you tried ifconfig in a terminal? (And is it possible to post the output here?) As you said you have more than one network adapter, could it be that you are configuring the wrong one?

---

### Post by Jormanks on 2007-03-11
sure i can outpost it here... 


eth0      Link encap:Ethernet  HWaddr 00:03:CE:89:E7:36  

          inet addr:200.118.190.153  Bcast:255.255.255.255  Mask:255.255.252.0
          	inet6 addr: fe80::203:ceff:fe89:e736/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6328 (6.1 KiB)  TX bytes:1881 (1.8 KiB)
          Interrupt:185 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:16:17:2D:E4:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2192 (2.1 KiB)  TX bytes:2192 (2.1 KiB)

---

### Post by Jormanks on 2007-03-12
Up!

---

### Post by Jormanks on 2007-03-14
Up....?

---

### Post by SactoBob on 2007-03-15
It sounds like you are running VMWare player with the live CD.  
That has to be very frustrating, With your equipment, you have enough resources to be happy running Ubuntu in a virtual machine - not the live CD.

Visit easyvmx.com and create a virtual machine which you extract to your hard drive.
Point VMWare Player to the virtual machine and use the Live CD to actually install Ubuntu into the virtual machine.  Don't worry when Ubuntu says it will partition the hard drive - it is talking about the VIRTUAL hard drive since you are in the virtual machine.  Your Win installation will not be damaged.

Now the virtual machine will work just about the same as if it were running installed on the machine itself.  Your wireless in the virtual machine will just work, as you have noticed, since VMWare is able to channel the Windows wireless driver into your virtual Linux machine.

You may have some trouble installing the onboard Realtek 8139 in native Linux.  Theoretically, it should work, but i gave up on mine and just bought a solution that I knew would work.

---

### Post by Jormanks on 2007-03-15
> **SactoBob said:**
> It sounds like you are running VMWare player with the live CD.  
That has to be very frustrating, With your equipment, you have enough resources to be happy running Ubuntu in a virtual machine - not the live CD.

Visit easyvmx.com and create a virtual machine which you extract to your hard drive.
Point VMWare Player to the virtual machine and use the Live CD to actually install Ubuntu into the virtual machine.  Don't worry when Ubuntu says it will partition the hard drive - it is talking about the VIRTUAL hard drive since you are in the virtual machine.  Your Win installation will not be damaged.

Now the virtual machine will work just about the same as if it were running installed on the machine itself.  Your wireless in the virtual machine will just work, as you have noticed, since VMWare is able to channel the Windows wireless driver into your virtual Linux machine.

You may have some trouble installing the onboard Realtek 8139 in native Linux.  Theoretically, it should work, but i gave up on mine and just bought a solution that I knew would work.

Yup, i ran the live cd with vmware, just ran it, virtually, but after some time after that i installed ubuntu in the real Hard drive, restarting my pc and everything... last saturday evening.. and, as you said, .... there are troubles with that netcard...

Maybe if I get another?
I could switch between cards but.... i don't know... there are so many things I have to change in windows ...

...

---

### Post by SactoBob on 2007-03-15
You could get another card that would work well with both Linux and Windows.  Some people would rather die than spend money on more hardware, and will go without internet for months to make a card work.  I am at the other extreme, and just want something that works now.

Here are a couple of posts that may expose you to some ideas that you might not have considered for a wireless solution without drivers, and useful for either windows or Linux, or any other operating system.

[http://www.linuxquestions.org/questions/showthread.php?t=536554](http://www.linuxquestions.org/questions/showthread.php?t=536554)

[http://www.linuxquestions.org/questions/showthread.php?t=536898](http://www.linuxquestions.org/questions/showthread.php?t=536898)

Bob

---

### Post by Ocxic on 2007-03-15
try desabling one card they could be in conflict with each other, 

"sudo ifconfig eth0 down"

make eth0 eth1, if you want the other card turnd off, replace down with up to turn in back on.

---

### Post by Jormanks on 2007-03-15
> **Ocxic said:**
> try desabling one card they could be in conflict with each other, 

"sudo ifconfig eth0 down"

make eth0 eth1, if you want the other card turnd off, replace down with up to turn in back on.

I've tried. 

And no, it doesn't work.

> **SactoBob said:**
> You could get another card that would work well with both Linux and Windows.  Some people would rather die than spend money on more hardware, and will go without internet for months to make a card work.  I am at the other extreme, and just want something that works now.

Here are a couple of posts that may expose you to some ideas that you might not have considered for a wireless solution without drivers, and useful for either windows or Linux, or any other operating system.

[http://www.linuxquestions.org/questions/showthread.php?t=536554](http://www.linuxquestions.org/questions/showthread.php?t=536554)

[http://www.linuxquestions.org/questions/showthread.php?t=536898](http://www.linuxquestions.org/questions/showthread.php?t=536898)

Bob

Thanks man, but I don't have a wireless card and don't plan to buy one "yet". I'm thinking about buying a new one, a regular one (no wireless)... could you name some cards, give me some advice?
Well, a big advice!

Thanks guys, anyways

(I'm frustrated: the netcard my PC has is "supported" by Ubuntu. I mean, buying one was completely out of my mind)

---

### Post by SactoBob on 2007-03-15
I am sorry that I misread your post.
I assumed that you were having trouble with a wireless card.
I am new on this forum and forgot that it also covered wired cards.

I think I did this because it is unusual for Ubuntu to have a problem with a wired connection to the internet.  It sounds like you have already tried just plugging your cable into the other card.
So you are saying that neither card works with Ubuntu - I'm stumped.

---

### Post by Jormanks on 2007-03-15
As far as it goes, the cards are recognized but I can't seem to get any connections.

Anyway....

Thanks for your interest, honestly.

---

