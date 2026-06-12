---
title: "Wireless Problems"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2007-04-26
I've been trying to get my wireless network connection set up properly but it just doesn't seem to be going well for me. It's kind of ridiculous how much effort this is taking.

Okay, so I install Ubuntu. Conveniently enough, it detected my wireless card and gave me the option to connect to a wireless network. I click it, enter in the settings, and nothing. Okay, maybe it doesn't recognize paraphrases for some reason? Okie dokie, so I try the full WEP key. Nope, nothing.


Alright, same thing except this time lets do a manual config. Open it up, I see it doesn't accept paraphrases. Well, that's fine, I have no qualms about entering in the WEP key. So, I do, configure everything correctly, but yet again it did not allow me to connect.


Alright, so at this point I'm frustrated beyond belief because I heard configuring wireless this new version of ubuntu was supposed to be breezy... Instead it is very feisty.

So, I continue to play around and search through the different settings. I open up the network tools interface and see it has my network interfaces listed in there and I can configure them. So I try that, same settings I was entering before, and for whatever reason it allows me to connect. So, yippee it's all taken care of right? Not even close...


Now, everytime I restart the computer I lose the connection. It doesn't seem to save to the configuration file. And after the initial setup it is no longer a matter of just opening up the network tools and reconfiguring again. Not at all. I have to go back and forth between the manual configuration and the configuration option in the network tools and eventually one of them works. Perhaps I have to do a certain thing before I do this certain thing, I don't know, I haven't (and don't really care) figured out the nuances of this.


All I know is that this is extremely frustrating and if I cannot maintain my wireless connection on a consistent basis I may look for other options as far as the OS is concerned. I've always loved Ubuntu but this is too much work just to get my internet up and running.


Has anyone else experienced this problem? Any fixes?

---

### Post by BHelts on 2007-04-26
Hi, I had a similar problem, not with connecting, but staying connected through different sessions and reboots.  I tried wifi radar, and that worked well for me although i understand it's a bit buggy at times.  might be worth a try.

---

### Post by nickj6282 on 2007-04-26
Hi,

First of all "HAR!" on your puns. :lolflag: 

Next, what kind of wireless card do you have? Open up your terminal and type this command:

```

lspci > ~/Desktop/lspci.txt

```

This will create a new text file on your desktop called "lspci.txt". Copy and paste the contents of that file in here (preferrably inside a [ code ] [ / code ] block)

thanks and good luck!
-Nick

---

### Post by jaytek13 on 2007-04-26
```

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
01:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:08.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

```

It is a DLink card. I can't find the box and don't know the model # off hand, but I can take out the card if necessary.

And as a side not (this seems remotely pertinent) I disable the eth0 interface but it randomly re-enables itself even without a reboot, but a reboot will definitely lead to it being turned back on.

---

### Post by nickj6282 on 2007-04-26
Hmm, I was under the impression that Atheros wifi cards were supported by default. Does your wireless card list as "ath0" in your interfaces list?

---

### Post by jaytek13 on 2007-04-26
> **nickj6282 said:**
> Hmm, I was under the impression that Atheros wifi cards were supported by default. Does your wireless card list as "ath0" in your interfaces list?

Yes it does.

---

