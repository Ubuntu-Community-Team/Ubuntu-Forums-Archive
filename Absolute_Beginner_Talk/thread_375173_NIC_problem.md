---
title: "NIC problem"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kikapu on 2007-03-03
Hi,

i installed a US Robotics router last night in my Windows installation and i set it to work just fine. I created a dual-booted system, with Ubuntu and the already exiting Windows.

I made the same IP adjustments in ubuntu (like i have made in Windows) and i can not event communicate with the router through it's web interface, with Firefox.

Then i started to search and i went in "Administrator/Network tools" and i saw that as "Network Device" it says that it has "Loopback interface (lo)".

As i am now learning linux, does this mean that it did not correctly identify my network card (Broadcom Netlink 10/100/1000) ??
And what you, generally, do in situation like this in ubuntu ?

---

### Post by angryfirelord on 2007-03-03
Loopback is just the local inteface (ip address 127.0.0.1), which is not the nic.

The problem is that some cards work under Linux & some do not. You'll have to get the model number of your card & do some google searching (and/or post it here too).

---

### Post by kikapu on 2007-03-03
I just want to make sure that ubuntu did not identify the card.
If it did, the card would be displayed at the point that now i see the "loopback interface" ?

And if it did not, then why i am able to change ip and other settings in "Networks" ?

---

### Post by kikapu on 2007-03-03
I search the forum and found this command: 
sudo lshw -C network

in my machine, it gives me:
* - network :0 DISABLED
description Ethernet interface
product: Nextreme BCM5788 Gigabit Ethernet
...


Aha! So it DID find my network card...Apparenty is that the problem is this "network :0 DISABLED".

Does anyone knows how i can fix this ??

Thanks for any help!

---

### Post by angryfirelord on 2007-03-03
> **kikapu said:**
> I search the forum and found this command: 
sudo lshw -C network

in my machine, it gives me:
* - network :0 DISABLED
description Ethernet interface
product: Nextreme BCM5788 Gigabit Ethernet
...


Aha! So it DID find my network card...Apparenty is that the problem is this "network :0 DISABLED".

Does anyone knows how i can fix this ??

Thanks for any help!

Possibly. Type **ifconfig** and see what comes up.

---

### Post by kikapu on 2007-03-04
> **angryfirelord said:**
> Possibly. Type **ifconfig** and see what comes up.

I did and it gave me this:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Does it help you understand what is going on ?

Thanks -again- for the help!

---

### Post by HereInOz on 2007-03-04
Have you tried going to System > Administration > Networking and enabling the eth0 interface?  It may be all you need to do.  Sometimes you also need to set a static IP and enter the DNS servers in that area as well, to get the thing up and running.

---

### Post by kikapu on 2007-03-04
> **HereInOz said:**
> Have you tried going to System > Administration > Networking and enabling the eth0 interface?  It may be all you need to do.  Sometimes you also need to set a static IP and enter the DNS servers in that area as well, to get the thing up and running.

I have given there a Static IP and the correct DNS servers. I am not sure i have this choice that you gave me about enabling eth0 interface, i rebot now to ubuntu and tell you right away.

---

### Post by kikapu on 2007-03-04
What an idiot i am...I had enter IP address, DNS servers and i haven't done the most obvious thing: Just click the network interface to make it active...:lolflag: 

This reply is my first from ubuntu and it really feels great!

Thank you all again!

---

### Post by angryfirelord on 2007-03-04
> **kikapu said:**
> What an idiot i am...I had enter IP address, DNS servers and i haven't done the most obvious thing: Just click the network interface to make it active...:lolflag: 

This reply is my first from ubuntu and it really feels great!

Thank you all again!

:lolflag: 

Of course, if you wanted to do it the Debian way, you could have simply added the interface into /etc/network/interfaces. All it would have taken is two lines of this:
```
auto eth0
iface eth0 inet dhcp
```
If you ever want to use Debian, this is the way of activating it.

Good luck Ubuntu-ing!

---

