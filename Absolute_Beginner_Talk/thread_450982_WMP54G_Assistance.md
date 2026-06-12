---
title: "WMP54G Assistance"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-05-21
On the HardwareSupportComponentsWirelessNetworkCardsLinksys page ( [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) ) it has my wireless card, the Linksys WMP54G and says, "Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too."

Now I'm a very basic beginner at Ubuntu Linux, and I was wondering if anyone could give me simple, easy to understand steps, or point me in the direction of a guide to help me to get internet access on my Ubuntu system. Because for the past week, my Ubuntu system keeps freezing whenever I try to mess around with it's wireless features and it's very difficult for me to solve on my own, so any help would be much appreciated.

---

### Post by overdrank on 2007-05-21
> **dswhite85 said:**
> On the HardwareSupportComponentsWirelessNetworkCardsLinksys page ( [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) ) it has my wireless card, the Linksys WMP54G and says, "Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too."

Now I'm a very basic beginner at Ubuntu Linux, and I was wondering if anyone could give me simple, easy to understand steps, or point me in the direction of a guide to help me to get internet access on my Ubuntu system. Because for the past week, my Ubuntu system keeps freezing whenever I try to mess around with it's wireless features and it's very difficult for me to solve on my own, so any help would be much appreciated.

HI this thread may help 
[http://ubuntuforums.org/showthread.php?t=241565&highlight=WMP54G](http://ubuntuforums.org/showthread.php?t=241565&highlight=WMP54G)
And a search of the forums is great !!!!!!!!!;)

---

### Post by clinto on 2007-05-24
Okay, I've been reading all over the place and what I *could* understand didn't help me that much.

Here's my dilema: I'm working on my parents' pc. They had XP Professional installed, but it just went haywire yesterday(imagine that!). I'm not sure what triggered all simultaneous critical errors, but I'm not really worried about it neither. I wiped off their hard drive and used Gparted to prepare for an Ubuntu Feisty install. This is their partition table on a 40gb:

hda1 | 10gb for a future reinstallation of XP
hda2 | 15gb | ext3 | /home (which they will be able to access with Windows as well)
hda3 | 11gb | extended
hda5 | 10gb | ext3 | / Ubuntu Feisty
hda6 | 100mb | ext | /boot
hda7 | 1gb | linux-swap

I've installed Ubuntu and everything is beautiful. The only problem is internet access. I'd installed the Linksys WMP54G v4 before Windows went capoot. Ubuntu picks up my home network, but I can't get it to connect to it. 

From what I've gathered from [this chart](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys), it's detected as ra0 and I need to enter my router's information.

When I use **iwconfig**, it tells me indeed I'm using ra0, that my router is RT2500, my home network is listed in the ESSID, I have a link and my quality is good. But I'm unable to access the internet.

Earlier, I couldn't even draw a link to my home network. I'm not sure what changed, for I've been trying all sorts of things. I'd downloaded a driver, referred [here](http://ubuntuforums.org/showthread.php?t=241565&highlight=WMP54G), I'd unpacked it and used **make**.

I'm not using any kind of security, since there's not really anyone living around here to mess with it. I didn't want to make things any more difficult. However, I probably should learn how to use different security features. I didn't use the manual settings in Ubuntu's Network Settings, I'd left it on Enable roaming mode.

*edit*I checked the connection information and it doesn't list the ip address, subnet, dns, nothing except the interface, speed, driver and hardware address.*edit*
Do I have to disable the roaming mode and enter the wireless settings manually? Is this my problem or am I missing something else?

---

