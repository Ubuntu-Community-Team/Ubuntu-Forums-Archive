---
title: "More LAN help needed"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by wink on 2007-05-28
Thanks to previously provided help here I am now able to grab sound and graphics files from my Windows machine to the Feisty desktop. However, I still have an unresolved issue with the laptop. Here is my current LAN setup:

Computer A (desktop, wired connection) running Windows XP SP2
Computer B (desktop, wired connection) running Feisty
Computer C (laptop, wireless connection) running Feisty

The problem:
Feisty C can access the Internet, acknowledges the existence of the Windows A on the LAN but can't find Feisty B nor can B locate Feisty C. 

Result:
An utterly stumped Ubuntu newbie. 

As always, thanks for any help in advance.

---

### Post by Alterax on 2007-05-28
Probably best if we just start from the basics with this one:  The TCP/IP stack.

Is your wireless networking and your LAN device on the same router?  If they are, then we can skip a couple of steps. 

But could you post (private is OK) your IP address for each device, along with the network (or subnet) mask, and the gateway that each device gives you--in case you don't know how (I am assuming you do, but just in case) The Linux commands are:
  (probably) ifconfig eth0 (for the wired connection)
  (probably) ifconfig eth1 (for the wireless, usually this works).

  And on the Windows box, it's ipconfig /all

  Also, check to see if you  can ping the other computers from each other; that'll tell us more about what is going on under the hood.  (command is same for windows and Linux both, it's ping whatever.the.ip.addressis
although on Ubuntu I've noticed I have to stop it with CTRL-C)

Most likely, your computers may just be on different subnets (I see this a lot) but still have the gateways and DNS servers done properly.  That could explain why you are able to access the Internet, but not the other computers.

Let's see if we can work this out.

--Alterax

---

### Post by wink on 2007-05-28
Thanks for the quick response, Alterax. Since I have not found a way to post privately here, I will just let it  all hang out, such as it is.

First, yes all units - both wired and wireless - are on the same router. 

Computer A's (Windows) configuration is as follows:
IP Address 192.168.1.100
Subnet 255.255.255.0
Default Gateway 192.168.1.1
DHCP and Autoconfig are enabled
san.rr.com is my DNS

Computer B's IP address is 192.168.1.101, sub 255.255.255.0.  Since I'm posting from C (the laptop) and it won't talk to B, I could place its ifconfig results in a follow up post, if needed.  

The results from C (laptop)

ifconfig eth1
eth1: error fetching interface information: Device not found

so I did ifconfig ath0

ath0      Link encap:Ethernet  HWaddr 00:90:96:BA:DC:E7  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:feba:dce7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1098943 (1.0 MiB)  TX bytes:189584 (185.1 KiB)

BTW, you asked about pinging and the answer is yes, I can ping them all. I also believe you are correct, I had originally set up a separate wireless connection for the laptop (C) in order to secure it. 

Again, thanks for your help, I am looking forward to hearing more from you.

---

### Post by pmg on 2007-05-28
Are you saying that FeistyB and FeistyC an ping each other by IP address, but not by hostname?  If that's the case, it sounds like a hostname lookup problem.  Or are you able to ping by hostname but making some other kind of connection doesn't work, in which case what kind of connection is it you're trying to make?  Also, are you running a firewall?

---

### Post by wink on 2007-05-29
Yes, Feisty B and C can ping each other (as well as Windows A) but I've done it only using their IP addresses.  I will try using host names and if the results are different I will be sure to post them here. 

No, none of the three are running firewalls.

Thanks for responding. 

wink

---

### Post by wink on 2007-05-29
Update: None of the three can be pinged by host name. 

pmg: sorry I forgot to respond to part of your post:

> what kind of connection is it you're trying to make?

I am trying to make A (Windows) desktop accessible so I can transfer sound and graphics files to both the Feisty desktop (B) and laptop (C). It's working between A and B which are wired to the router but not C which is wireless.

wink

---

### Post by pmg on 2007-06-01
I thought I had posted another followup, but must have missed hitting the "submit" button.

I'm not quite following things here.  In your initial post you said Feisty-C can access the network and acknowledges Windows-A, but not Feisty-B. Likewise, Feisty-B cannot locate Feisty-A.  In a follow-up, you said they can all ping each other by IP address but not by hostname, and that you are able to access the Windows Desktop from Feisty-B, but not Feisty-C.

If you can ping all the the machines from each other, it's not a network setup/routing problem.  You said there are no firewalls so we can rule that out.  If Feisty-B and C can ping each other, what application are you trying to run that won't connect?  Maybe you don't have something configured to start.  There are lots of ways of sharing files between the systems.  I was just reading the thread [http://ubuntuforums.org/showthread.php?t=460281]("http://ubuntuforums.org/showthread.php?t=460281") about setting up SMB between systems.  Maybe that will give you some ideas.

---

### Post by wink on 2007-06-02
> I thought I had posted another followup, but must have missed hitting the "submit" button.

Not to worry, I've been guilty of that myself.;)

As to the rest, I am happy to report that the problem has been solved and my laptop can now access the files on A (Windows). I still have no idea where that extra / [slash] after smb kept coming from in the Windows Network File Browser, but that was the culprit. Blame it on my eyes that will be celebrating their 77th birthday in a couple of months and I wonder if that makes me the oldest newbie around here?

Thanks anyway for picking up the thread again.
wink

---

