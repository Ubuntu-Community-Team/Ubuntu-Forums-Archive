---
title: "How can i get my ip back on windows."
date: 2012-03-31
forum: Any Other OS
---

### Post by beceraful on 2012-03-31
do you understand about windows , i have a problem with the windows network, there my ip is 169.254 , instead 87.120......
in the first 2-3 months , i have network on the windows and my ip on windows and linux still was 87.120...... , but now on linux my ip is 87.120... but on windows is 169.254 and i do not have network. How can i made my  ip 87.120.... but in linux to be too 87.120.... when was in the first 2-3 months.. please tell me , of course if you know

Thanks ;)

---

### Post by 2F4U on 2012-03-31
Since you provide no information about how your network is setup, you won't get much response. What is your network infrastructure and what is providing IP addresses to your machines?

---

### Post by chili555 on 2012-03-31
In both Windows and Linux, the IP address 169.254.x.y means, approximately, "I tried to get an IP address from the router/modem/access point, but there is something wrong with my configuration and the router/modem/access point says it can't connect me."

What exactly is wrong on the Windows side is beyond my knowledge. I suggest you check and compare settings. I doubt this is the best place to troubleshoot *Windows* networking.

---

### Post by beceraful on 2012-03-31
Look , 4 months my ip on windows and linux was 87.120.... , then when the 5 month comes my ip on windows changes on 169.254 , i'm not doing nothing , i don't understand about options and other things i want only to make my ip on windows 87.120.... and my network to come back , and Linux-s IP to be 87.120.... like windows. Windows and linux with one IP as in the first months

---

### Post by tehchibipanda on 2012-03-31
Its pretty much what chilli said. If I'm not mistaken, 169.254 is more or less your connection going to Narnia, and you have to clean up route tables, manually assign the IP address, etc...

[http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/0a108825-b3ae-4541-993b-d239a1a7ce1e/](http://social.technet.microsoft.com/Forums/en-US/w7itpronetworking/thread/0a108825-b3ae-4541-993b-d239a1a7ce1e/)

Little bit of google magic, for you

---

### Post by beceraful on 2012-03-31
but what i have to do.. I don't know i do not have experience.. 

With one word , does the problem can be solved , with one word again on windows and linux to be the IP 87.120.... no change with one word again?

---

### Post by haqking on 2012-03-31
169.254 is a APIPA address in Windows, its called a zeroconfig (link local) address in Linux.

It is assigned by the machine to itself when it has the TCP/IP stack set to find one from a router/DHCP serever etc and cant find one.  It allows it to still function on a network but is not routable.

You need to check your own IP settings to see where the issue is as top why you  are not being assigned an address or enter the IP address you want manually.

Cheers

---

### Post by tehchibipanda on 2012-03-31
If I'm not mistaken, the problem is on the windows side of your machine. 169.254 is on that side, whereas linux has your regular IP, correct? You could always call tech support for router tables/ipconfig/etc help. or turn to Google and look up how to manually assign an IP address in whatever windows OS you are using.

---

### Post by beceraful on 2012-03-31
I don't understand what to do when i log into windows 
ok i see your theories but i want to know that will have a chance to be the ip 87.120.... like in linux but now in windows to ? With one word Windows and linux with one ip. Yes or no or i will have to "delete" Linux to get my internet on windows back?

---

### Post by haqking on 2012-03-31
> **beceraful said:**
> I don't understand what to do when i log into windows 
ok i see your theories but i want to know that will have a chance to be the ip 87.120.... like in linux but now in windows to ? With one word Windows and linux with one ip. Yes or no or i will have to "delete" Linux to get my internet on windows back?

This is not a windows forum.

Depending on your version of Windows go to the properties of the LAN connection and check your IP settings there and apply a static one if needed.

Or check your DHCP server for issues.

Or consult with a windows forum.

Cheers

---

### Post by howefield on 2012-03-31
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by bubylou on 2012-03-31
Windows 7
Control Panel - Network and Internet - Network and Sharing - Change Adapter Settings - Local Area Connection - Properties - Internet Protocol Version 4 (TCP/IPV4). 

IP address - 87.120....
Subnet mask - 255.255.255.0 (depending upon your own network configuration)
Default gateway - routers ip address

Preferred DNS server - router or other DNS server

 I have no idea what kind of network your running so your going to have to fill in the blanks. Also the Linux and Windows machine cannot have the same ip if they will both be on at the same time.

---

### Post by beceraful on 2012-04-01
I want only to have internet on the windows , thank you for the information , they i don't know but i want only to download some musics and to talk in skype with friends , i rarely will get on windows , i am always in linux because my cs server is on it. i want only to download music then i agreed to not have network (internet) . 

With one word the ip can't be on linux and windows ?? as was in the first 4 months when i installed linux ? 

If the ip can't be one in linux and windows , can i made  another IP in windows and have internet ??

in cmd inconfig/renew , if i write it what will going to do , everything will be that i want ??  

Thanks. And pls post a new reply in the thread , thank you again

---

### Post by chili555 on 2012-04-01
If you have two separate computers connected at the same time with one running Linux and the other running Windows, the IP addresses cannot be the same; they can be in the same neighborhood, for example 87.120.xx.3 and 87.120.xx.4.

If you are dual-booting *one* computer and sometimes you run Windows and other times you reboot into Linux, you *can* have the same address.

If you are connected directly to a DSL or cable modem, with only one ethernet port, the modem can't be connected to more than one computer at a time anyway, so it won't matter. Looking at your IP address, 87.120.xx.yy, I suspect that's the case.

---

### Post by beceraful on 2012-04-01
Look , if i write in windows ipconfig/renew , do we give me a new ip on windows and the internet will be working well ?? About the linux nothing wrong wouldn't going to happend? I mean if i write it in cmd ipconfig/renew do we give me a new ip but the Linux will be hurt ? I mean the ip will change or something else or nothing or the linux will be normally with this ip that i am at the moment ? 

With one word if i write in the cmd ipconfig/renew the system or what is there do he give me a new ip and do i will have internet , and if yes , the linux will something happend or nothing , the ip will still been 87.120.... or ? 

Pls tell

---

### Post by haqking on 2012-04-01
> **beceraful said:**
> Look , if i write in windows ipconfig/renew , do we give me a new ip on windows and the internet will be working well ?? About the linux nothing wrong wouldn't going to happend? I mean if i write it in cmd ipconfig/renew do we give me a new ip but the Linux will be hurt ? I mean the ip will change or something else or nothing or the linux will be normally with this ip that i am at the moment ? 

With one word if i write in the cmd ipconfig/renew the system or what is there do he give me a new ip and do i will have internet , and if yes , the linux will something happend or nothing , the ip will still been 87.120.... or ? 

Pls tell

changing your IP in Windows has nothing to do with Linux unless both are running at the same time.

Also the address 87.120.x.x i am guessing is a ISP assigned address and not a LAN address so you dont have much control over it.

As already mentioned your questions seemed to be windows related and would be better i a windows forum.

---

### Post by beceraful on 2012-04-01
ok thanks by the way

---

### Post by CharlesA on 2012-04-01
> **haqking said:**
> changing your IP in Windows has nothing to do with Linux unless both are running at the same time.

Also the address 87.120.x.x i am guessing is a ISP assigned address and not a LAN address so you dont have much control over it.

As already mentioned your questions seemed to be windows related and would be better i a windows forum.
This, pretty much.

I would reset your modem/whatever and/or contact your ISP to make sure everything is good if the modem reset doesn't work.

---

### Post by bubylou on 2012-04-01
If you could explain how exactly you are connecting to the internet and tell us how your network is setup it would be much easier to help your solve your problem. Like haqking said if your having a windows issue then its would be better served in a windows forum or try Google.

---

### Post by beceraful on 2012-04-01
I only wanted on windows to have network , 1 person told me this thing , Start>Run>cmd>ipconfig/renew , but he didn't tell me more , i know only that if i write this in the black console it will give me IP and i will have internet , but i don't know is that true, 
or should do more things to do this thing and have Internet. He told me that linux's ip (REAL IP) won't be changed or somethink else , no problems with 1 word , but i don't know is this true. 
Pls tell if that is true and what more i have to do to have network on windows. I want to have network on windows 1-2 days max.

---

### Post by CharlesA on 2012-04-01
> **beceraful said:**
> I only wanted on windows to have network , 1 person told me this thing , Start>Run>cmd>ipconfig/renew , but he didn't tell me more , i know only that if i write this in the black console it will give me IP and i will have internet , but i don't know is that true, 
or should do more things to do this thing and have Internet. He told me that linux's ip (REAL IP) won't be changed or somethink else , no problems with 1 word , but i don't know is this true. 
Pls tell if that is true and what more i have to do to have network on windows. I want to have network on windows 1-2 days max.
Huh?

All ipconfig /renew does it renew your IP with the DHCP server. If your ip address is really 87.x.x.x then you would have to deal with your ISP support to get it working, as that isn't a private IP (one that you get from a router).

---

### Post by coffeecat on 2012-04-01
@beceraful, I want to draw your attention to this:

> **bubylou said:**
> If you could explain how exactly you are connecting to the internet and tell us how your network is setup it would be much easier to help your solve your problem.

+1

Details of your internet connection, please. Broadband or dial-up or mobile? If dial-up, details of modem. If broadband, adsl or cable? If broadband, how do you connect to your modem-router - wired or wireless?

---

