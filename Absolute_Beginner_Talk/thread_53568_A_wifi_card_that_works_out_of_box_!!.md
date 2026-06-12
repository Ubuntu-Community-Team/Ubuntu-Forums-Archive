---
title: "A wifi card that works out of box ?!?!?"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-08-01
I've got a D-Link DWL-G250 that is "works out of box" according to this list:
[https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards)

It didn't work so I did this for my (rev 01) card:
Atheros AR5212 Madwifi HowTo
[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=DWL-G520](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=DWL-G520)

didn't work so I did this:
SetupNdiswrapperHowto
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

it shows up in Networking now and I put my WEP info in and still nothing. I even made the router have no WEP and completely open thinking that was the problem. and nothing.

I don't have time to play with this anymore. I've got 7 days before I can get my money back. I've already wasted two days playing, config, rebooting and searching.

This is the second card that I've gotten. The first one was a linksys wmp54gs (or something like that).

Is there any card that REALLY works out of the box with Hoary??

thanx

---

### Post by poofyhairguy on 2005-08-01
[QUOTE=xnszxdotnet]I've got a D-Link DWL-G250 that is "works out of box" according to this list:
[https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards)

It didn't work so I did this for my (rev 01) card:
Atheros AR5212 Madwifi HowTo
[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=DWL-G520](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=DWL-G520)

didn't work so I did this:
SetupNdiswrapperHowto
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

it shows up in Networking now and I put my WEP info in and still nothing. I even made the router have no WEP and completely open thinking that was the problem. and nothing.

I don't have time to play with this anymore. I've got 7 days before I can get my money back. I've already wasted two days playing, config, rebooting and searching.

This is the second card that I've gotten. The first one was a linksys wmp54gs (or something like that).

Is there any card that REALLY works out of the box with Hoary??

thanx[/QUOTE]

Does it have to be a 802.11G card? All of my 802.11b Prism cards work great.

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by xnszxdotnet on 2005-08-01
as of now I don't care. I would like it to be "g" for faster internal networking. I'm not really going to be on the web that much. I want to put MythTV on this box / rip /burn DVD record TV etc.

Is there a card that will just work without all this other ndiswrapper stuff?

I'd love to just go get this card, put it in, and cont. with my life.

like I said I don't have time to play around with stuff.

---

### Post by poofyhairguy on 2005-08-01
[QUOTE=xnszxdotnet]as of now I don't care. I would like it to be "g" for faster internal networking. I'm not really going to be on the web that much. I want to put MythTV on this box / rip /burn DVD record TV etc.

Is there a card that will just work without all this other ndiswrapper stuff?

I'd love to just go get this card, put it in, and cont. with my life.

like I said I don't have time to play around with stuff.[/QUOTE]

For 802.11b the link I gave you will give you clues (anything that is Prism should be ok). For 802.11g the only thing I know are these:

[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

---

### Post by tymek666 on 2005-08-01
Mine cheap Dlinik 520+ works 'out of the box' very well. But it supports only 11 Mb and 22 Mb connection (b standard).

---

### Post by Mr. Electric Wizard on 2005-08-02
Hey man, can you post the whole model number for this adapter please?
I think your referring to D-Link DWL-G520, is this correct?

I want an adapter that WILL WORK.

---

### Post by tymek666 on 2005-08-02
[QUOTE=Mr. Electric Wizard]Hey man, can you post the whole model number for this adapter please?
I think your referring to D-Link DWL-G520, is this correct?

I want an adapter that WILL WORK.[/QUOTE]

No, mine is DWL-520+. Belowe is some desciption from dlink site:

'The D-Link AirPlus DWL-520+ PCI Adapter is an enhanced 802.11b adapter featuring advanced silicon chip technology from Texas Instruments. The DWL-520+ is fully compatible with the IEEE 802.11b standard making it interoperable with all existing 802.11b compliant devices. Now you can transfer files or communicate up to 20% faster than previous 802.11b solutions, even when connected to a standard 802.11b network. When you’re connected to other D-Link AirPlus products, the maximum wireless signal rate of up to 22Mbps* can be achieved. '
Best wishes

---

### Post by xnszxdotnet on 2005-08-02
I'm thinking of this Belkin F5D6001 pci card. 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

says it's a Prism2/2.5/3 chipset. Can I assume that since it's prism chipset that I can get it to work with little work with Hoary? 

I hope so. It's so very frustrating. I SOOOO don't want to have to go back to windows. I've had one to many blue screens  :? 

feedback on this card would help alot.
thanx

---

### Post by Juergen on 2005-08-02
Well, it would have helped to see the output of iwconfig and ifconfig for your card.
And maybe your /etc/network/interfaces.
(I don't trust GUI-tools for configuration, at least check what they have done...)

I have a 'levelone wnc-0300' and got it to work without problems, even with WPA.
(for the WPA config, I had no options in the GUI-tool, so I **had** to do a bit of editing manually. Maybe you should get used to that...)

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=xnszxdotnet]I'm thinking of this Belkin F5D6001 pci card. 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

says it's a Prism2/2.5/3 chipset. Can I assume that since it's prism chipset that I can get it to work with little work with Hoary? 

I hope so. It's so very frustrating. I SOOOO don't want to have to go back to windows. I've had one to many blue screens  :? 

feedback on this card would help alot.
thanx[/QUOTE]

ALL non USB Prism cards I have tried work out of the box.

---

### Post by xnszxdotnet on 2005-08-02
[QUOTE=poofyhairguy]ALL non USB Prism cards I have tried work out of the box.[/QUOTE]

good thing you said non-USB because I was also looking at the Netgear MA311 (USB prism card)

I would hate havin to go back to the store again. 

Thanks, again I'm gonna order that Belkin f5d6001 card after all.

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=xnszxdotnet]
Thanks, again I'm gonna order that Belkin f5d6001 card after all.[/QUOTE]

Be careful. Looking at the list I provided it seems that only the first version of the card is Prism. The newer versions are not, and I know from experiance that the other cards don't work easily (realtek is a big pain in the ass).

I personally wanted what you wanted. I bought a WMP11 off ebay that was advertised as an older version. Works better than in Windows.

If you are buying this card new....they might give you a new version and your pain starts again....think about using ebay.

---

### Post by poofyhairguy on 2005-08-02
I found this:

[http://users.linpro.no/janl/hardware/wifi.html](http://users.linpro.no/janl/hardware/wifi.html)

---

