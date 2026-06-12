---
title: "[SOLVED] Nooby needs help with wifi"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by ockron on 2007-05-19
Thank you for those who helped me in getting Feisty Fawn installed.

I am not trying to get my Wireless Network card going.

I hope I provide enough information.
This desktop was wirelessly connected to my ADSL router at home. The installation went very well: sound card, dial-up modem, CD-writer... everything was recognised and correctly installed by Ubuntu.... This is quite a success as now I can startup/shutdown the computer without the computer crashing... But the wireless NIC, a Realtek 8185 sold as a Dick Smith XH8343 here in New Zealand, has not been recognised: 
I am eager to get that working so that I can use the printer from my laptop through the network (This is the challenge after the wireless NIC installation ;-)).

Reading through the help files I see that I can use *ndiswrapper* that is part of the installation CD. I used System --> Administration --> Synaptic Package Manager. But I could not locate it.
I downloaded the file *ndiswrapper-1.44.tar.gz* and copied it to a CD, but I don't know how to access it or use it.
How to I activate/locate and use this?

Please be patient with a new convert!!

I have access to the internet from my laptop (I'm using it now)

---

### Post by chamberlain2006 on 2007-05-19
Your original post was misleading.  It didn't you do not need to install the wireless NIC.  Instructions to do so are 
[here.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

---

### Post by ockron on 2007-05-19
I'm sorry.
I'm not sure what you mean with the misleading part.

This link shows that my card is supported by Ubuntu.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-751ff8f98030df97347576e45ed468055b1e3fe3](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-751ff8f98030df97347576e45ed468055b1e3fe3)

When I go to System --> Administration --> Networks. I cannot see my network card.

---

### Post by chamberlain2006 on 2007-05-19
> I am not trying to get my Wireless Network card going.
You continued on about your wireless, so I assume you mean that you are NOW trying to get it working.  Anywho, let's get busy with your wireless.  Can you please post the output of lspci (if your card is internal) or lsusb (if your card is USB).  Strip out the parts except the part pretaining to your card.

---

### Post by ockron on 2007-05-19
Sorry about that .. Its a slip of the finger I meant I am now trying to get the wireless going.

The Card is a PCI card.
 A Realtek 8185 sold as a Dick Smith XH8343 here in New Zealand.

---

### Post by chamberlain2006 on 2007-05-19
Ok.  Seems you need to use NdisWrapper.  Its pretty easy.  Just do the command I tell you in Terminal (Applications>Accessories>Terminal)
```

sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
wget ftp://209.216.61.149/cn/wlan/x86-8185\(1094\).zip
unzip x86-8185\(1094\).zip
sudo ndiswrapper -i net8185.inf
sudo ndiswrapper -l 
sudo ndiswrapper -m
sudo modprobe ndiswrapper
iwconfig
Go to System>Administration>Networking to configure your interface (wlan0)

```

---

### Post by ockron on 2007-05-19
Is that all one long command, or do I have to break it up as in the txt.

As soon as I push enter it tries to execute the command typed

---

### Post by chamberlain2006 on 2007-05-19
You have to execute each line individually.

---

### Post by ockron on 2007-05-19
When I execute the command -
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common

I get the following message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

---

### Post by chamberlain2006 on 2007-05-20
You do have an internet connection, don't you?

---

### Post by drowner on 2007-05-20
> **chamberlain2006 said:**
> You do have an internet connection, don't you?

He's talking to you, isn't he? ;)

---

### Post by ockron on 2007-05-20
Yes.

It used to work fine when I had XP installed.

How can I get ndiswrapper to work?

---

### Post by drowner on 2007-05-20
> **ockron said:**
> Yes.

It used to work fine when I had XP installed.

How can I get ndiswrapper to work?
The error you got before whilst installing ndis-wrapper was because you weren't connected to the internet.

Do you have a non-wireless way connecting to the internet?

---

### Post by ockron on 2007-05-20
I have downloaded ndiswrapper 1.44 and wrote it to a CD.

---

### Post by oxygenfarm on 2007-08-05
I also have the tew-424ub and got as far as "sudo ndiswrapper -l' but then goof where at the statement 'install the driver described by inffile'.
Help appreciated.

---

### Post by ockron on 2007-08-06
:( I've given up.
Maybe I'm just not meant to use Ubuntu??

---

