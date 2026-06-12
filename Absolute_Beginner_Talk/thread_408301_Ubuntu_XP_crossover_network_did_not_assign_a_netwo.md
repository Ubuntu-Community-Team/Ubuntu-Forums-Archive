---
title: "Ubuntu XP crossover network did not assign a network address to the computer"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-04-13
OK, I have plugged an ethernet crossover cable from my ubuntu PC to m XP laptop.  The XP laptop (which I am talking to you from) says that I have limited connectivity because "network did not assign a network address to the computer.  The ubuntu PC hasn't said anything.  Clicking repair does nothing.  What should I do?

---

### Post by jgrabham on 2007-04-13
ok maybe someone could just talk me through setting up a peer to peer network?

---

### Post by Grout58 on 2007-04-13
Are you positive its a crossover cable?

---

### Post by jgrabham on 2007-04-13
the guy in the shop said it was

---

### Post by Daveski on 2007-04-13
Networking is quite a complex subject. Your XP machine will not get an IP address assigned to it as you have no DHCP server set up. If you want 2 machines to talk over a cross-over cable, then both machines need to have static IP addresses in the same subnet - e.g. 192.168.8.1 and 192.168.8.2.

You should be a bit more specific about what you are trying to do - and be patient - 1 hour is not too long to wait for free support.

---

### Post by Grout58 on 2007-04-13
Do the laptops have wireless?

---

### Post by jgrabham on 2007-04-13
ok, so how do I make them have "a static ip address in the same subnet"?

I dont even know what a subnet is!

---

### Post by jgrabham on 2007-04-13
> **Grout58 said:**
> Do the laptops have wireless?

one does, so wireless isnt an option!

---

### Post by Grout58 on 2007-04-13
In ubuntu you will have to edit the /etc/networking/interfaces config file, I think they may also be a gui option in networking.

In windows you will have to go to manage network connections > right click the connection > go to properties > click tcp/ip > hit properties and fill it in.

---

### Post by Daveski on 2007-04-13
> **jgrabham said:**
> ok maybe someone could just talk me through setting up a peer to peer network?

Got to the network settings in both XP and Ubuntu. Change the options from 'Obtain IP address automatically' to Static (or user defined). Add these:

1 machine:
IP address 192.168.8.1
subnet 255.255.255.0

2nd machine:
IP 192.168.8.2
SN 255.255.255.0

EDIT: It is MUCH simpler to have both machines set to automatic and have a broadband router assign IP addresses to all machines attached to it. Do you have a Router?

Now you should be able to ping both these addresses from both these machines. This means that the underlying IP networking system is working. Now what do you need to do with the networked machine? Share files?

Windows can see Linux shared folders if you install the add-ons to allow you to do so. Ubuntu can see windows shared folders by default - go Places, Network.

To share a folder on your Ubuntu machine that the windows machine can see is a bit more complex and requires you to install and setup the Samba server under Ubuntu.

Does any of this help?

---

### Post by jgrabham on 2007-04-13
i have the internet on the windows pc and want to get it on the ubuntu pc

---

### Post by jgrabham on 2007-04-13
> **Daveski said:**
> 
EDIT: It is MUCH simpler to have both machines set to automatic and have a broadband router assign IP addresses to all machines attached to it. Do you have a Router?


Ive tried a router before, and it didn't like my broadband! (talktalk)

---

### Post by jgrabham on 2007-04-13
OK ive just changd the IP addys to 192.168.0.1 and 192.168.0.2 because windows said I need to have it on 192.168.0.1 to share the internet connection.  But theres still no internet on ubuntu.  Do I have to do something on Ubuntu?  (at the moment Im just opening firefox and trying to go on [www.google.com](www.google.com))

---

### Post by Daveski on 2007-04-13
> **jgrabham said:**
> OK ive just changd the IP addys to 192.168.0.1 and 192.168.0.2 because windows said I need to have it on 192.168.0.1 to share the internet connection.  But theres still no internet on ubuntu.  Do I have to do something on Ubuntu?  (at the moment Im just opening firefox and trying to go on [www.google.com](www.google.com))

Ah, you are doing Internet Connection Sharing on the Windows machine. In this configuration you should be able to either set the IP on the Ubuntu machine as you have - but make sure that the Default Gateway is set to the IP of the Windows machine (192.168.0.1). Or you could set the Ubuntu machine to Automatic DHCP as the Windows machine will be acting as a DHCP server and assign clients compatible addresses.

I have seen problems with Windows ICS where it does not correctly allow clients to resolve Domain Names (the DNS component does not always work with ICS in my experience). To solve this you could set the client machines (Ubuntu in your case) to static DNS addresses - this will be provided by your ISP - or just check the current Windows (the ICS machine's) DNS settings - use IPCONFIG /ALL at the Windows Command Line.

Have you got any experience of running IPCONFIG or PING and TRACERT on Windows? These are basic troubleshooting tools to see which components of your network work (or don't).

---

### Post by jgrabham on 2007-04-14
In case you havnt noticed, im not very good at networks. i know the dns is something to do with my isp but thats about it.  What do i put in the dns boxes?

---

### Post by Daveski on 2007-04-14
You should see the Windows machine has 1 or 2 IP addresses of your ISP's DNS servers. Find these and put them in the DNS setting of the Ubuntu machine. DNS is the address your machine uses to ask: What ip address is [www.website.com?](www.website.com?) The DNS server should reply with an IP address.

[www.google.co.uk](www.google.co.uk) is currently 66.249.93.99 so if your DNS is not working [http://www.google.co.uk](http://www.google.co.uk) will give a page not found error, but [http://66.249.93.99](http://66.249.93.99) might load the initial page (the rest of the site it unlikely to work properly though without a working DNS).

Type *ipconfig /all *at the Windows command prompt. Write down the IP addresses listed under *DNS Severs.....*
Put these addresses in the DNS section of the Ubuntu's network config.

---

### Post by Daveski on 2007-04-17
Any joy?

---

### Post by Austin_KW on 2007-04-17
If you are using windows internet connection sharing (in its default setup) it should run a mini dhcp server. You should not have to set static ip addresses. The ubuntu should then automatically set its configuration (ip,mask,dns,gateway)
Try turning off any firewalls on the windows PC. Some firewalls block the gateway functionality needed to share the connection.

---

### Post by jrhendri on 2007-06-12
Very helpful.  Thank you!

---

