---
title: "Getting Linux to work with a wireless network"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by tkpmep on 2006-02-26
I have just installed the latest Dapper Drake Alpha on a slightly elderly Dell Dimension XPS T450 that lacks a network card. I'd like to integrate it into my home network and connect to the Internet. I have a Two Wire HomePortal 1000SW wireless router (SBC, my DSL provider, gave it to me), and I'm looking for some advice on PCI wireless cards. Two questions:

1. What wireless cards work with Linux and SBC/Yahoo DSL?
2. Once I install the card, how do I configure it to talk to the router?

Thanks in advance

Thomas Philips

---

### Post by nalmeth on 2006-02-26
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
this is a troubleshooting guide for breezy, but it should still be good for dapper.

For dapper related questions you should post here:
[http://ubuntuforums.org/forumdisplay.php?f=111](http://ubuntuforums.org/forumdisplay.php?f=111)

Good luck to ya

---

### Post by nickle on 2006-02-26
[quote=tkpmep]

1. What wireless cards work with Linux and SBC/Yahoo DSL?
2. Once I install the card, how do I configure it to talk to the router?
[/quote]

I am by no means an expert but I will try to give you some tips:
[LIST=1]
[*]Search this site for wifi, there are many useful threads. This is what I did to get going.
[*]There two main ways the wifi cards are currently supported in linux: 1) using native linux drivers; 2) Using windows drivers which are incorporated in the kernel using a program called ndiswrapper. The reason for the latter is that many, if not most wifi cards do not yet have native linux drivers written for them.
[*]I would recommend finding a card that has native linux support. It will make your life much easier. Cards with atheros chips have native support and I am sure there are others. Again a search will probably help here. This might be a good place to start: [http://madwifi.org/](http://madwifi.org/)
[*]A problem is that is is usually not possible to see what chip is in a card by looking at the box and forget ask in most stores :). Here is a link for cards the work: [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
[*]For example I bought a D-link DWL-G520, put it in my machine, booted up and it was recognised immediately.
[*]On KDE if you go to the menu button you will find system settings. There you will find networksettings.
[*]Having installed your card, it should show up here if it is supported.
[*]Then you go to administrator mode and go through the menu settings just like you would in windows.. Save and reboot. If you are lucky it should be working.
[*]Then type in ifconfig and you should get an output like this:[ATTACH]6454[/ATTACH]
[*]Ath0 refers to the wifi card. If you do not see inet *addr:192.168.2.100* i.e. the IP address that has been assigned to your card then type: *sudo dhclient ath0* where ath0 is the device name assigned to the card. This will assign an IP and from then on you card should be working
[*]As I say I am not an expert, but this is what I did to get my card working and it went very easy.
[*]Please read around if you really want to understand more. This is a great forum for such things and please feel free to post again if you have problems: *the only stupid question is the one you are afraid to ask...:)  Good luck*[/LIST]

---

### Post by tkpmep on 2006-03-07
I bought a DLink GL-520 card and installed it, and Ubuntu recognized it. It remained only to fix the networking. I clicked on System > Networking, chose Wireless Connection and clicked on Properties. My SBC/ TwoWire DSL wireless network showed up. I chose Hexadecimal for Key Type (not sure why, but ASCII does not work) and then found that I did not know the WEP encryption key. I eventually discovered that the WEP encryption key was the 10 digit number located on the underside of my TwoWire HomePortal Router. It appears that this number must be input with 2 dashes, i.e. as 1234-5678-90. I then chose DHCP under Connection Settings > Configuration and I could connect to the internet. 

Works like a charm with only one glitch:  when I restart the computer, the WEP key gets lost and has to be re-entered. 

Question: what do I need to do to ensure that Ubuntu remembers my wireless key? I really don't want to type it in each time I start the machine.

Thomas Philips

---

