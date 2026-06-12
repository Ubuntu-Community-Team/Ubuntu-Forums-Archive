---
title: "Internet Connection won't succeed"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by nschmitz06 on 2008-03-27
I'm new at Ubuntu and just put gutsy 7.1 on my Toshiba laptop and i cant figure out for the life of me how to get the internet to work. Ive looked at many different guides to the internet and other peoples posts but have found nothing to work. I have another computer that i surf the internet on so i can deal with the problem quite easily without having to reboot into windows to talk back. Please help me configure my Ethernet connection. Thank you.

---

### Post by Pevichaey5 on 2008-03-27
wat is you ether cable plugged into?

if its ur router, are you obtaining an ip by dhcp or is it manually configured?

---

### Post by nschmitz06 on 2008-03-27
i have it plugged into a Netgear wireless router, that is plugged into a Linksys modem. we have cable, from comcast. The computer I'm talking to you with is also connected into the Netgear router.

---

### Post by m60dude5 on 2008-03-27
Hi. I'm new at the Ubuntu thing too, but I had similar problems, soo. Anyway, check in the Hardware Information (System, Preferences, Hardware Info) and see if your network card is recognized. If so, then use the network utility (click on the little computers in the panel) and add your IP, the router's IP, etc, Then hit connect. If that doesn't work, let me know.

---

### Post by nschmitz06 on 2008-03-27
it shows both my wireless card and marvell ethernet card as onboard network interfaces. however, nowhere does it show my ip dns, etc, the closest thing i can find to anything usefull is a mac address, but i only used that in windows.

---

### Post by nschmitz06 on 2008-03-27
in windows i received my ip by DHCP. so i would assume the same for ubuntu

---

### Post by m60dude5 on 2008-03-27
Ok. So it recognizes your cards, which is good. If so, forget ndiswrapper. Click on the connection icon, and choose "manual configuration" in the box that comes up, right click on your wired connection and choose properties. That is where you need to enter your DNS server info, your ip, etc. First, try choosing "static ip" and entering an ip your router supports. Then, under default gateway, add the ip of your router, usually 192.168.1.1 

let me know if this works

---

### Post by nschmitz06 on 2008-03-27
that didnt work

---

### Post by m60dude5 on 2008-03-27
Ok then. Let's see... Is your connection recognized? I mean, when you click the computers, there is a drop down menu. Is your connection listed there under wired connections? 

Another thing to try, there are four tabs when you click manual configuration: Connections, General, DNS, and hosts.
See the screen shot I have:
On the Hosts tab, click add and add the ip of your router. 

Reply with the following information.

Your computer's ip address and whether it is static or dynamic
Your router's ip
The name of your connection

Once you have that, I can walk you through... hopefully.
I'll include screenshots as well from my experience.
I won't be online until tomorrow since its pretty late here, but I will check tomorrow around lunch time. Let me know that info above and we'll get started.

---

### Post by nschmitz06 on 2008-03-27
it didn't work. heres my info

my ip, 192.168.1.6
subnet mask 255.255.255.0
gateway address 192.168.1.1
-------------------
i went into my router settings and it has a few different type of address groups. here they are

Internet Port  
MAC Address  00:0F:B5:A2:75:27 
IP Address  24.15.181.223 
DHCP  DHCPClient 
IP Subnet Mask  255.255.240.0 
Domain Name Server 
 68.87.72.130
68.87.77.130
 
LAN Port 
MAC Address  00:0F:B5:A2:75:26 
IP Address  192.168.1.1 
DHCP  ON 
IP Subnet Mask  255.255.255.0 

Wireless Port  
Name (SSID) NETGEAR 
Region United States 
Channel 08 
Mode Auto 
Wireless AP ON 
Broadcast Name ON 

-------------
I am currently connected to the Lan Port

thanks and let me know what i can do to fix this

---

### Post by superprash2003 on 2008-03-28
are you able to ping.. go to the terminal and type ping google.com and post results here

---

### Post by m60dude5 on 2008-03-28
Alright. There are a bunch of settings in that box screenshot I showed you, and missing one of them may cause the problem you're having. 
I am not at my computer now, but I'll reply by 5 tonight when I can get to it. That way I can see what the box says. So far, I rooted out the info you'll need from the info you gave me. Here it is:
your ip address, which is 192.168.1.6
your router's ip, which is 192.168.1.1
subnet mask of 255.255.240.0

the other information is regarding your router connecting to the internet, the 24.15.181.223 is an external address, which you won't need for the setup.

One other thing you can try until I reply, is changing the router to assign one ip address per computer. For example, I have four computers in my house. In the router setup, I assigned static ips to each of them so: kitchen 192.168.1.2  etc. This means, each time I connect with that computer, it uses the same ip. This may allow you to enter more settings in Ubuntu, so that it provides the router with its ip, instead of the other way around. I wouldn't recommend changing anything unless you know how to do it, and how to get it back if it doesn't work.

I apologize for not being able to help you promptly with this, work schedules don't let me get home until 5 and I don't remember what each screen says exactly.

Good luck, and I'll get back to you.

---

### Post by m60dude5 on 2008-03-28
> **superprash2003 said:**
> are you able to ping.. go to the terminal and type ping google.com and post results here

I don't think he can get on to his network, so he wouldn't be able to get internet either, if its through router. But if your wireless works...

---

### Post by m60dude5 on 2008-03-28
Ok. Here it is, step by step, with some screenshots too. 
1. Single click on the two computers, the network icon.
2. Click Manual Configuration
3. In the box that comes up, click the connections tab
4. Right click on wired connection and choose properties. See screenshot 1.
5. In the box that comes up, enter the info exactly as I did in screen2
6. Click okay
7. In the box, click the general tab and make sure your host name is listed and domain name is blank. Don't change whatever is in the host name box.
8. Now click the DNS tab.
9. Add both of your DNS servers, which are: 68.87.72.130 and 68.87.77.130
10. Do that by clicking add and typing them one at a time
11. If there are any others, delete them
12. Now click the hosts tab.
13. Click add. type 192.168.1.1 in the box and under aliases type "router"
14. Don't do anything else in that box. Click close.
15. Click on the computers. Is your connection listed?
16. Thats the best I can do. If it isn't let me know if you want to try wireless we can do that as well. Best of luck.

---

### Post by Mr noodle on 2008-03-28
I just installed v7.1 on a Compaq M700. My Airlink card set up out-of-the- box,  read all the nearby connections, but like you wasn't able to get connected. After fiddling with the Network Settings, I get a message saying the interface configuration is being changed, then wammo...it connects. Here are my settings in the Network Settings box:


Under the connections Tab: Wireless Connection box is checked
Network Name: Linksys
Password Type: WEP Key (ascii)
Configuration: Automatic Configuration (DHCP)
Under Hosts Tab: Localhost is highlighted
Under DNS Tab: the DNS server address appears 

What confuses me is nowhere do I see any light, icon or indicator on the desktop indicating  I am connected. 
Shouldn't there be something there?

---

### Post by nschmitz06 on 2008-03-28
thats what i did have it set up with and ive tried almost anything else including some things in the terminal program. I dont know know why it wont connect, i can boot windows on the same laptop do wireless and regular lan to both my router and modem individually, but nomatter how i try to configure it in ubuntu it wont do anything. i could try wireless setup and hope for the best, but i know ill have to install ndiswrapper which i already tried and decided that since nothing worked i did another full install and started from scratch, but still nothing works. all i can come up with is, windows is so much easier to deal with until ubuntu can straighten out all these internet problems.

---

### Post by nschmitz06 on 2008-03-28
also, the bar in any window i open is like two inches thick with huge letters that never finish what its supposed to say for the window, what is up with this terrible enlargement?

---

### Post by nschmitz06 on 2008-03-28
also also, for my wireless when i first tryed to set it up, when it was on roam it didnt work, so i tried to put it on dhcp, but then it asked for a password and security type, but my wireless has no security in it and now i have to go through the trouble of putting passwords all over hell for ubuntu to connect, but it still wont. why is it that everything in ubuntu is such a pain in the *** to install through flash drive, i have the linux version of my wireless nic but i have no idea how to install it, and the install file is always so vague that it doesnt help at all!

---

### Post by Mr noodle on 2008-03-28
With your card plugged in, and Enable Roaming unchecked, does your connection appear in the Network Name box?

---

### Post by nschmitz06 on 2008-03-28
im running a laptop, so the card is always in, and it is turned on, at least in windows it was. and what network name box? i cant find one at all, im running gutsy 7.1

---

### Post by m60dude5 on 2008-03-28
Sorry that didn't help you, I am as stuck as you are. He means the network name box that drops down when you click the computers icon.

---

### Post by m60dude5 on 2008-03-28
> **Mr noodle said:**
> 
What confuses me is nowhere do I see any light, icon or indicator on the desktop indicating  I am connected. 
Shouldn't there be something there?

Mr. Noodle,
Yes, if you are connected, if wireless, there should be a status bar indicating strength once you are connected.

---

### Post by nschmitz06 on 2008-03-28
there is no network name box

---

### Post by m60dude5 on 2008-03-29
Are you using Gusty Gibon? Click the computers once. A box drops down. That's the box we're talking about. Its okay if there's no networks listed, it's still the network name box.

I don't know what to tell you. Did you try wireless yet? You said it recognized your card, so you shouldn't need ndiswrapper, since that helps it recognized your card. Look at the screenshot on my next post and I'll show you the network name box.

---

### Post by m60dude5 on 2008-03-29
Here is the box I get when I click the computers once. Your computers should be where my little wireless status bar is.

---

