---
title: "dhclient connection problems"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by frostbytes on 2007-08-20
Hey all, I have a problem and I was wondering if anyone out there could help me fix it.  I created an ad-hoc network on my XP box.  My Fiesty laptop picks up the signal well, and it even tells me that someone is connected to me on my XP box when I go through the command line and enter the key and what not.  Now my only problem is when I run the dhclient, I get 100% packet loss, thus no internet connection.  Thanks for any help

---

### Post by cmnorton on 2007-08-20
Does your XP box have the dhcp service running?

---

### Post by frostbytes on 2007-08-21
I am pretty certain that it does, I mean, I can get on the internet on it, other than that I dont know.

---

### Post by cmnorton on 2007-08-21
In order for dhclient to get an address, some dhcp server has to serve an address. 

I believe your XP system has to be some flavour of Windows server, unless you have installed a DHCP service on the system. If you goto my computer->Manage, and look for services, you should see if the dhcp service is installed. You will see a dhcp client.

---

### Post by frostbytes on 2007-08-21
alight i checked and it the there....do i need to change some options or something to make it send the client out with the wifi signal?

---

### Post by cmnorton on 2007-08-22
If you have a wireless network, there is probably a dhcp server in your cable or dsl modem or in the router.

---

### Post by frostbytes on 2007-08-22
actually im retarded...i looked in manage, i saaw dhcp and didnt look at the word after it.  i have a dhcp client on my windows machine, i need to get a dhcp server on there so that my other machine can find the internet.  any idea how I would go about that, or better, any way to make this work an easier way

---

### Post by Austin_KW on 2007-08-22
> **frostbytes said:**
> actually im retarded...i looked in manage, i saaw dhcp and didnt look at the word after it.  i have a dhcp client on my windows machine, i need to get a dhcp server on there so that my other machine can find the internet.  any idea how I would go about that, or better, any way to make this work an easier way

Turn on Internet Connection sharing on the windows PC, tell it to to share its internet connection with the wireless adapter; this will enable a mini dhcp server on the windows PC and basic NAT router type functionality. Then windows will give the the feisty box an address and route its traffic to the 'net. Takes a couple of clicks.(i think it is, right click the internet connected adapter in control panels, select properties, select advanced, but not sure don't use windows much) or you can use the wizard.

Simple really, ;)

---

