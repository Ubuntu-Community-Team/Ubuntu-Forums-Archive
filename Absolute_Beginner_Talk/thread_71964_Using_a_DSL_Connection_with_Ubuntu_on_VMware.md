---
title: "Using a DSL Connection with Ubuntu on VMware"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by Gadren on 2005-10-04
I profusely apologize for this query, which I'm sure has been asked many, many times before, but I couldn't find any help from searching the forums.

I'm using VMware v5, and have installed Ubuntu 5.04 on it.  It boots up great, but my issue is my Internet connection.

I use a DSL modem from SBC Yahoo! DSL, and I can't get it to work with Ubuntu on VMware.

Running **sudo pppeoconf** hasn't helped -- with my Ethernet as "bridged," pppoeconf will go through the entire setup, but Firefox will not connect to the Internet.  Both NAT and Host-only end the setup prematurely (right after the scanning for devices section) with the following message:

"NOT CONNECTED
Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem."

I know that my DSL connection works (because I'm using it on my WinXP installation right now!), and I had also been able to get my DSL in Ubuntu on VMware working before (before an unfortunate hard drive reformatting).

Is there something like an XP service that has been accidentally disabled that's needed, or something of that like?

Please help quickly -- I would very much like to learn more about Linux and Ubuntu.

---

### Post by brentoboy on 2005-10-04
if i remember correctly, vmware puts an icon in thier program group for configuring the bridged network.

I think that that is the best place to start.

---

### Post by Gadren on 2005-10-05
I've looked around there -- but I've no idea what any of it means (networking is one area of computer experience I'm not skilled in).  I've tried fiddling with some of the settings, but I haven't gotten it to work.
After I do **pppoeconf**, I type in **plog**, as it recommends, and I get the following:
[img]http://img362.imageshack.us/img362/4650/ubuntu2tq.gif[/img]

---

### Post by brentoboy on 2005-10-05
Before I kick in and try to help, understand that my vmware experience amounts to about 2 weeks of use, and about 4 months of listening to my brother tell me how great it is.  That said, lets dig in and fix it.

I think your biggest problem is the pppoe.  It should be unncessary.

Your Host computer (windows) is your connection to the world, and the hosted virtual computers get to see the world through him, like a gateway. (I think)

If this is not default, it is an option.

The bridged network allows the virtual PC to have a public IP address on the same network as the host computer.  Which means you would need to use DHCP (or pppoe) to connect to the internet via the virtual machine.

But I think there is an option to let the host pc act as a routher/dhcp server, and all the virutal pcs just get assigned ip adresses, and as long as the host is connected to the internet, the virual machines are too.

does that make sense?

--
All that said, My vmware is expired, and I cant test out my comments and be more helpful, but I hope that this gives you something to start digging on.  Sorry I couldnt be more helpful.

---

### Post by Gadren on 2005-10-05
Well, I've discovered another interesting issue -- when I try to load up an OS in bridged, I get the following error:

The network bridge on device VMnet0 is not running.  The virtual machine will not be able to communicate with the host or with other machines on your network.
Virtual device Ethernet0 will start disconnected.

---

### Post by DravenHavok on 2005-10-05
Hi, I'm abolutely new to Unbuntu and Linux. And I'm trying it out with the live cd. I liked it very much and would like to keep it, however, I couldn't figure out how to make my internet connection work either. I also have an SBC Yahoo DSL line like Gadren does. And I looked  for other posts trying to figure out what to do, but to no success. I found myself here, and I thought I would jump in and ask for help. I looked up for the VMware thing but didn't know exactly what it was, or what it did. So could someone explain to me what's going on? And how I go about getting my internet to work on Unbuntu? Thanks in advance.

---

### Post by Gadren on 2005-10-06
I got it working!  I just had to disable my XP connection, then I could connect with VMware on Ubuntu... :D

And DrakenHavok, I would not recommend VMware, or any kind of virtual machine, unless it's your only option.  All OSs will run slower on VMware, for example.

---

### Post by DravenHavok on 2005-10-06
So how do I go about using my Internet on Unbuntu? Could you be so kind as to explain to me? Anyone? Please? ^_^

---

