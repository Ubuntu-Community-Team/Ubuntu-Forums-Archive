---
title: "Ubuntu and Wireless"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by ally_uk on 2007-11-05
Hi Guys 
I'm going to be setting up 7.10 tonight I have a D-link 802.11G wireless router which I will be connecting up via Ethernet.

What is the procedure for setting up the internet is it fairly straight forward?

Many Thanks

Ally

---

### Post by ushills on 2007-11-05
If you are connecting from the router to the PC via the Ethernet cable then the setup should be straight forward.

If you have not yet set up the router follow the manufacturer's setup guide, you will be able to set it up via Firefox, use the settings from your ISP.

If you have already set up the router then just try it an post any problems.

If you are going to use a wireless connection you may run into problems depending on the wireless card in your PC.  Again post any problems and you will generally get advise.

Some initial thoughts:

test you can ping your router:

Something like 

```
ping 192.168.1.1
```

Then test if you can ping a website

```
ping www.google.com
```

if you have problems post the outout of the following individual commands

```

lspci
iwconfig
ifconfig
cat /etc/resolve.conf
cat /network/interfaces
```

---

### Post by so7777777os on 2007-11-05
> **ushills said:**
> If you are connecting from the router to the PC via the Ethernet cable then the setup should be straight forward.

If you have not yet set up the router follow the manufacturer's setup guide, you will be able to set it up via Firefox, use the settings from your ISP.

If you have already set up the router then just try it an post any problems.

If you are going to use a wireless connection you may run into problems depending on the wireless card in your PC.  Again post any problems and you will generally get advise.

Some initial thoughts:

test you can ping your router:

Something like 

```
ping 192.168.1.1
```

Then test if you can ping a website

```
ping www.google.com
```

if you have problems post the outout of the following individual commands

```

lspci
iwconfig
ifconfig
cat /etc/resolve.conf
cat /network/interfaces
```
Very helpful to me,too.  Many thanks..

---

### Post by ally_uk on 2007-11-05
Appreciate this guys I will post up some feedback tonight!

---

### Post by ally_uk on 2007-11-05
Just a quick query when I go into the terminal and try and ping a website I get no results

On a windows box for example you get results saying packets sent and lost etc, but on my Ubuntu box it says pinging Google but I get know results.

Is this expected?

---

### Post by smurphy_it on 2007-11-05
Anytime I've tried to ping something and get no reply usually means your network is down in some form.  Simplest being no IP address for your NIC (wifi).

Without exact info on what your specific setup is for wifi/wired no-one could help too much.

For example, is this wired or wireless (if wireless is it native wifi or using ndiswrapper).

Follow the steps at the beginning of this thread for starters.

---

### Post by ally_uk on 2007-11-05
No this is my Ubuntu box I'm using at work it's a static I.P, network and internet activity are both working there is also a Squid proxy caching websites.

Although when I try and ping a website I get no results could this be because of restricted privileges on the machine? as the SYSADMIN has locked it down for security reasons.

For example I don't have root acess.

---

### Post by smurphy_it on 2007-11-06
Sysadmin could have pinging disabled.

---

