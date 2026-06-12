---
title: "Network problem killing my will.."
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by muzcuk on 2006-02-04
Hey, I am trying to get into this linux thing for a while now. I have a history on C programming so I really enjoy learning this thing. It gives you total control and power over everything and there are all this people around the world willing to help you. But I have a problem now. I just got a new laptop. It is a compaq presiaro V2000z with an AMD turion processor and broadcom wireless lan and ATI Radeon Xpress 200m graphics. All these three components have problems with linux. I love dealing with that kind of problems, reading forums and trying to figure out how they work but there is this network problem and its killing me. 

I normally use wireless network with windows. I found some howtos to show me how to make it work in linux, but I need to download stuff with apt-get, so I need my wired network to make my wireless network work. But whenever I plug my wired network in and reboot, linux doesn't recognize my network as I expect it to do. I'd expect it to get an ip from the dhpc server on the boot up process and make internet available for apt-get. It doesn't, so I guess I have to set it up myself somehow. But I never messed with network stuff in linux so I'm kind of clueless about it. 

I don't have display nor internet on my linux system now. I am thinking if I can get the wired network work, then I can get the wireless work, and then I can make the graphics chip work. I can do all this with howtos and stuff, but now, because I don't have my network setings, I have to keep switching between windows and linux so it's killing all my will to work on this. Please just give me a clue on where to start for this network thing, I'm familiar with networks, I'm good at them on windows, but I never worked on them on linux. I'm really amazed that it didn't get an ip by itself. 

Thanks

---

### Post by bscbrit on 2006-02-04
On the commandline type:

man interfaces  :-D

---

### Post by alamba on 2006-02-04
After you have your LAN plugged in...on the commandline:

1. ifconfig
2. netstat -rn
3. Ping router/next hop

Maybe a description of how u're connecting to the internet would help.

Akshay

---

### Post by muzcuk on 2006-02-04
I have cable modem connected to a wired/wireless router. Modem is 192.168.100.1, router is 192.168.0.1, DHCP server gives adresses starting 192.168.0.100, so the desktop at the living room is 192.168.0.100 and laptop is 192.168.0.101. I don't want to be mean but please don't give me a list of commands. Or if you do, write little explainations for each command, I hate just writing stuff and hitting enter without knowing what I am doing.

---

### Post by alamba on 2006-02-04
explanations = google
quick solve = forums (unless something not normally found in google)

Next steps:
1. Results of the steps above
2. Ping 192.168.0.1
3. Ping 192.168.100.1
4. Ping 4.2.2.2
5. Ping oracle.com
6. Paste here

A

---

### Post by muzcuk on 2006-02-04
I reconfigured xorg so I get it to work using vesa settings, then when I got my display working I went to system>administration>networking, then I configured and activated eth0, now it's working flawlessly. 

I would realy apreciate if you can tell me what we were trying to do with ifconfig and netstat -rn commands, because when I typed ifconfig, I got some weird IP adresses, when I typed netstat -rn, I got an empty iptable. I guess that was not what you expected. It changed after I configured the network though, now they make sense.

---

### Post by alamba on 2006-02-04
ifconfig <network interface name> e.g. ifconfig eth0 will show me the following:
1. Has your network card been initialized
2. Do you have an IP from your DHCP server

netstat -rn will show:
1. Routing table - Does it correspond correctly with the IP address shown above.

If these 2 things are right and assuming no layer 1 error - you should typically be able to ping atleast your gateway.

Post that I try to ping the internet via IP and if that is ok then u're probably missing DNS entry in your resolv.conf. Fix that and you should be online.

Hope that helps.

A

---

### Post by muzcuk on 2006-02-04
I see, ifconfig and netstat shows us if our ethernet card is configured right or not. But what if they are not configured right? I solved the problem with the graphic interface. It said my eth0 card was not "configured", so I configured it, then it sait my eth0 is "disabled", so I enabled it. But I did all these by clicking around, how would I "configure" and "enable" my ethernet card if I couldn't get to the graphical interface?

Now I'm trying to make my wireless network card work (damn you broadcom!) using ndiswrapper, if I have configured the eth0 manually, I would have an idea about how this stuff works, now I have a working network but no clue about what happened.

And another question, whenever I type "make" in the teminal, I receive several errors, I never had to do anything to use command "make" before but I think I'm missing a package or something now. I'm on windows right now, so I can't tell what error and I know you can't help me without knowing, I'll post it as soon as possible. 

note : I have build-essential, what else do you think I might need?

---

### Post by alamba on 2006-02-04
several commands help you "configure" and "enable" your card. I suggest you read up on google or "man interfaces" on ubuntu command line. e.g. ifconfig eth0 <ipaddress> up, etc. etc.

Maybe u're missing the kernel header files. Typically I type my kernel name on synaptic and install the sources.

A

---

### Post by bscbrit on 2006-02-04
Which Broadcom card are you trying to set up?  I configured the Belkin G last weekend, perhaps I can help?

---

