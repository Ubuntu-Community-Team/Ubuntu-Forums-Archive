---
title: "WPA for Linux"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by gizmom on 2007-12-13
As a brand new Linux user (using 7.04) I need a simple guide to how to get linux to connect to my wireless network via WPA. When i look in network manager the network is there but i can only get options to enter WEP data, not WPA, please can someone help?

---

### Post by coffeecat on 2007-12-13
Some wireless chipsets work fine with WPA in Linux/Network Manager. The Intel 2200BG in my laptop does, for example. Other chipsets - usually where the manufacturer is less than interested in providing useful information to the developer community - are more difficult to get working.

To find out what chipset your wireless card is using, open a terminal and issue the command:

```
sudo lspci
```You'll be prompted for your password. Look for the line with 'wireless' or '802.11' in it. That's your chipset. Post that and someone will be able to give you more specific information and/or search the forum with the chipset details.

Good luck!

**Edit:** I was assuming you're using an internal wireless card or built-in laptop wireless device. If you're using a wireless USB device, just substitute the above command with:

```
sudo lsusb
```

That's a lower-case L, not a number 1, at the beginning of lspci or lsusb, by the way.

---

### Post by stchman on 2007-12-13
> **gizmom said:**
> As a brand new Linux user (using 7.04) I need a simple guide to how to get linux to connect to my wireless network via WPA. When i look in network manager the network is there but i can only get options to enter WEP data, not WPA, please can someone help?

I need to ask this question.  I am going to assume that the wireless network you are connecting to is a router in your home.  If yes, did you setup the router to use WPA?  The Network Manager will identify the type of encryption and ask the proper information.  If you setup the router to use WEP it asks for the WEP key.

I set my router up to use WPA2, but when I go over to my friend's house he has WPA.  In each instance NM identifies what each system uses.

---

### Post by gizmom on 2007-12-14
You are correct in assuming that i am trying to connect to the wireless router in my home, it is set to use WPA and my WIndows machine works fine with it but in linux Network manager only gives me the option to input connection details for WEP.

I have done as suggested above and found the chipset, the line reads

RaLink RT2561/RT61 802.11g PCI

Does this help anyone help me?

---

### Post by coffeecat on 2007-12-14
I've found two links for you. I'm afraid they might seem a bit daunting to someone new to Linux. I'm surprised, because I thought Ralink was one of the more Linux-friendly wireless chipsets. Oh well. :sigh:

This one [from the Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61") is over a year old, but is probably worth looking at.

This [forum howto]("http://ubuntuforums.org/showthread.php?t=563547") is more recent, and has 25 pages of follow-up posts if you're feeling up to it. :? Your RT61 chipset is in the list.

You might want to see if anyone with direct experience of Ralink cards has anything to add before you embark on this.

---

### Post by stchman on 2007-12-14
> **gizmom said:**
> You are correct in assuming that i am trying to connect to the wireless router in my home, it is set to use WPA and my WIndows machine works fine with it but in linux Network manager only gives me the option to input connection details for WEP.

I have done as suggested above and found the chipset, the line reads

RaLink RT2561/RT61 802.11g PCI

Does this help anyone help me?

Apparently someone else has your card and solved the problem.

[http://ubuntuforums.org/showthread.php?t=586408](http://ubuntuforums.org/showthread.php?t=586408)

---

### Post by spiderbatdad on 2007-12-14
there is a package in synaptic called wpa-supplicant you might need. Also i believe i read another article where the key had to be entered as hex-code

---

### Post by stchman on 2007-12-14
> **spiderbatdad said:**
> there is a package in synaptic called wpa-supplicant you might need. Also i believe i read another article where the key had to be entered as hex-code

You should not need to do anything to enable WPA in Feisty or better.  As long as your wireless card supports it then you are good to go.

---

### Post by gizmom on 2007-12-18
I have been trying to follow the instructions from the ubuntu wiki that coffecat suggests and everything is going okay, i have had to puzzle out a few bits by trail and error and can now successfully ping my router, however i can't follow the establish a DNS instruction as when i enter $sudo echo "nameserver GATEWAY_IPADDRESS" >> /etc/resolv.conf i get the message back "permission denied" (i am aware that i have to put my gateway ipaddress in in place of the words GATEWAY_IPADDRESS above). But i seem to have reached what looks promising as being the last hurdle, anyone got any ideas?

---

### Post by seventhc on 2007-12-18
In mine if i go to manual configuration, then go to the properties of my wireless I can choose wpa which is what i am on now. You don't have that option there??
Mine is set to dhcp

---

### Post by spiderbatdad on 2007-12-18
> **gizmom said:**
> I have been trying to follow the instructions from the ubuntu wiki that coffecat suggests and everything is going okay, i have had to puzzle out a few bits by trail and error and can now successfully ping my router, however i can't follow the establish a DNS instruction as when i enter $sudo echo "nameserver GATEWAY_IPADDRESS" >> /etc/resolv.conf i get the message back "permission denied" (i am aware that i have to put my gateway ipaddress in in place of the words GATEWAY_IPADDRESS above). But i seem to have reached what looks promising as being the last hurdle, anyone got any ideas?

can you run the command as su rather than using sudo?

---

### Post by gizmom on 2007-12-20
no i cant run the command at all

---

### Post by gizmom on 2007-12-20
Hi everyone,

I would like to say a big thank you to everyone who has given me suggestions on how to set up my wifi in Ubuntu using feisty and a WPA wireless card with the RT61 chipset.

I have now found the perfect solution and would like to share it in case anyone else is suffering as i have. I have downloaded and installed Ubuntu 7.10 (gutsy) instead of feisty and my network was detected and configured at installation and now works brilliantly, even better than on windows.


Once again thanks for all your help

---

