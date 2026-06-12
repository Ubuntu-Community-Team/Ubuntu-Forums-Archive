---
title: "Internet and USB help"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by JSC714 on 2005-09-13
I just installed Ubuntu onto my computer today, but am a little confused. I've only worked with windows, so this seems like learning how to operate a computer all over again. My first question is, we have three desktop computers, two of them are windows and as of today the third one is Ubuntu. Our internet is run by a linksys wireless router. Will I be able to use linksys to have wireless internet with ubuntu? 

My second question, I'm having problems usuing the USB with Ubuntu. I tried to load a few pictures from the USb and I just couldnt figure it out. With windows something pops up when I plug something into my USB, but not with Ubuntu. Is there another way to acess the USB?? 

Thanks in advance :)

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=JSC714]I just installed Ubuntu onto my computer today, but am a little confused. I've only worked with windows, so this seems like learning how to operate a computer all over again. My first question is, we have three desktop computers, two of them are windows and as of today the third one is Ubuntu. Our internet is run by a linksys wireless router. Will I be able to use linksys to have wireless internet with ubuntu? [/QUOTE]

Depends. What wireless device (card or whatever) will use use to connect to the router in Ubuntu? Version and model number please.

> 
My second question, I'm having problems usuing the USB with Ubuntu. I tried to load a few pictures from the USb and I just couldnt figure it out. With windows something pops up when I plug something into my USB, but not with Ubuntu. Is there another way to acess the USB?? 


From a card reader, a camera, a pen drive? More details please.

---

### Post by numberexhaust on 2005-09-13
I agree... get as much information about your hardware as possible, and we will be able to help you.

---

### Post by awaldraff on 2005-09-13
Hi, maybe in th meantime you can help me... I am having this very same problem...

I am a complete newby in Linux, so pls be as specific in your response as you can..

I have a netgear WG311 adapter, and I am trying to connect to a netgear WGT series router..

My network is encrypted with a 128bit WEP key and I also have MAC address control enabled...

when I installed ubuntu, it found the network adapter, and I gave it the network SSID and the WEP key, however it replied that it could not connect to the network..

---

### Post by numberexhaust on 2005-09-13
[QUOTE=awaldraff]Hi, maybe in th meantime you can help me... I am having this very same problem...

I am a complete newby in Linux, so pls be as specific in your response as you can..

I have a netgear WG311 adapter, and I am trying to connect to a netgear WGT series router..

My network is encrypted with a 128bit WEP key and I also have MAC address control enabled...

when I installed ubuntu, it found the network adapter, and I gave it the network SSID and the WEP key, however it replied that it could not connect to the network..[/QUOTE]
 Please post the output of the command:

ifconfig

from your terminal window here.  Also, post the output of the command:

lspci

And let us know.  It would also be advisable to dig out the CD that came with your adapter, as it may prove useful.

---

### Post by Nequeo on 2005-09-13
[QUOTE=awaldraff]Hi, maybe in th meantime you can help me... I am having this very same problem...

I am a complete newby in Linux, so pls be as specific in your response as you can..

I have a netgear WG311 adapter, and I am trying to connect to a netgear WGT series router..

My network is encrypted with a 128bit WEP key and I also have MAC address control enabled...

when I installed ubuntu, it found the network adapter, and I gave it the network SSID and the WEP key, however it replied that it could not connect to the network..[/QUOTE]
 Hi, Awaldraff. 

You really ought to post a new thread for this kinda thing. It makes it easier for other people with the same problem to find the answer, rather than having to dig through posts with unrelated topic names.

However, from what I remember of the Ubuntu installer, it seems more likely that your card couldn't configure itself quickly enough over DHCP, than that it couldn't connect to the network. If that's the case, try setting your IP address manually by following the instructions here:

[http://www.ubuntuguide.org/#configurenetworkconnections](http://www.ubuntuguide.org/#configurenetworkconnections)

If you're tech savvy enough to have MAC filtering on your wireless network, I'm going to assume you know what settings you'll need. However, if that's not the case, feel free to ask for help. But please, do start a new thread for that.

Cheers,

---

### Post by awaldraff on 2005-09-13
hi, thanks for your prompto reply..

i will start a new thread as suggested...

---

### Post by JSC714 on 2005-09-13
Thanks for the replies, and sorry for the lack of information. 

The wireless card I'll be putting into the computer with Ubuntu as the OS is a Linksys Wireless - G PCI adapter model number: WMP54G 

Will that work? When I put the card in, and the installation CD, and tried to install it, it said it couldnt be installed.

---

### Post by numberexhaust on 2005-09-13
Don't have much time to post right now, but I can help you more later.  Please post the output of ifconfig and lspci, when you have booted with the card inserted in the computer.

---

### Post by JSC714 on 2005-09-14
How do I find the output of ifconfig and lspci? *embarassed* sorry, I'm not very knowledgeable when it comes to computers.

---

